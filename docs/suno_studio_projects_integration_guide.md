# Suno Studio Project Integration Guide

The Suno Studio Project API manages multi-track music projects through a single endpoint:

```http
POST /suno/projects
Authorization: Bearer YOUR_API_KEY
Content-Type: application/json
```

The `action` in the request determines the operation type. The Project primary key consistently uses `id`; `version_id` represents the current project version, and all modification and export operations must submit the latest version to avoid concurrent overwrites.

## Operation Overview

| action             | Mode  | Purpose                                      |
| ------------------ | --- | -------------------------------------------- |
| `create`           | Sync  | Create an empty project                      |
| `retrieve`         | Sync  | Read the project and complete editable `state` |
| `save`             | Sync  | Save the complete project state               |
| `upload`           | Async | Initialize assets that can be added to a project from an HTTPS audio URL |
| `add_track`        | Async | Add existing audio to a project               |
| `generate_track`   | Async | Generate new track candidates for a specified range |
| `replace_section`  | Async | Generate local replacement candidates         |
| `commit_candidate` | Async | Commit the selected candidate to the project  |
| `remove_track`     | Sync  | Delete the specified track                    |
| `render`           | Async | Export a saved version as a complete song     |

Async operations immediately return a `task_id`. Use the free `/suno/tasks` endpoint for polling, or pass `callback_url` to receive final-state results.

## Create and Retrieve

```json
{"action":"create","title":"My Studio Project"}
```

All modification operations should send a unique `Idempotency-Key` Header. After successful creation, `data.id` in the response is the Project ID. A newly created empty project may not have a `version_id` before its first save.

```json
{"action":"retrieve","id":"PROJECT_ID"}
```

The retrieval response contains the complete `state`. A newly created empty project returns `{"tracks":[],"timing":{"bps":2}}`, which can be used directly for the first save. `timing.bps` represents beats per second, with a default of 2 (120 BPM), and must be positive; a clip's `startBeats`, `endBeats`, and `readStartBeats` use project beat units, and measure positions in audio analysis cannot be directly treated as timeline coordinates.

## Save Complete State

```json
{
  "action":"save",
  "id":"PROJECT_ID",
  "version_id":"CURRENT_VERSION_ID",
  "title":"Edited Project",
  "state":{"tracks":[],"timing":{"bps":2}}
}
```

The first save of a newly created empty project may omit `version_id`; after the first save generates a version, subsequent saves must submit the latest value. If the version has changed, the API returns HTTP 409. In this case, `retrieve` again, merge the changes, and submit using a new idempotency key; do not blindly retry the old request.

## Upload and Add Tracks

```json
{
  "action":"upload",
  "id":"PROJECT_ID",
  "version_id":"CURRENT_VERSION_ID",
  "audio_url":"https://cdn.example.com/reference.mp3",
  "async":true
}
```

After a successful upload, read the audio ID from `response.data.candidate.audio_id`. Then add it to the project:

```json
{
  "action":"add_track",
  "id":"PROJECT_ID",
  "version_id":"CURRENT_VERSION_ID",
  "audio_id":"AUDIO_ID",
  "name":"Backing Vocals"
}
```

Adding a track preserves the audio playback speed by default and converts the audio duration into beats according to the project's `timing.bps`. After every `save`, `add_track`, `commit_candidate`, or `remove_track`, use the new `version_id` in the response.

## Generate and Replace

`generate_track` generates track candidates for a project range; `replace_section` returns two local replacement candidates. Neither operation automatically selects the artistic result. Models must use public names: `chirp-v3-5`, `chirp-v4`, `chirp-v4-5`, `chirp-v4-5-plus`, `chirp-v5`, `chirp-v5-5`, `chirp-v6`, `chirp-v6-wild`, or `chirp-v6-mini`; availability for specific operations is still subject to the task final state, unsupported names return 400 before submission. It will not automatically switch to another model.

```json
{
  "action":"replace_section",
  "id":"PROJECT_ID",
  "version_id":"CURRENT_VERSION_ID",
  "source_audio_id":"AUDIO_ID",
  "start_seconds":35.12,
  "end_seconds":48.76,
  "model":"chirp-v6",
  "replacement_lyrics":"New lyrics segment",
  "async":true
}
```

`generate_track` must also provide `render_audio_id` (completed project export audio), `stem_control_tags`, and source audio `source_audio_id`. `batch_size` is 1–4, with a default of 2; `start_seconds` and `end_seconds` are source audio seconds. A replacement range with `fixed=true` must be shorter than 26 seconds.

Commit after selecting a candidate:

```json
{
  "action":"commit_candidate",
  "id":"PROJECT_ID",
  "version_id":"CURRENT_VERSION_ID",
  "operation_id":"OPERATION_ID",
  "candidate_id":"CANDIDATE_ID",
  "track_id":"TRACK_ID"
}
```

Candidates are bound to the project version at the time of generation. Once the project has changed, old candidates cannot be committed directly.

Local replacement candidates are committed to the original track containing the unique source clip, and complete take candidates retain the original position while replacing the original clip; range candidates replace only the requested range while preserving the clips before and after it. If duration cannot be matched reliably, 400 is returned and the original project is retained; in this case, do not pass `start_beats` or `end_beats`. New-track candidates should be committed to an empty track saved in advance, defaulting to the source clip start point, or explicitly provide a non-overlapping range; overlapping existing clips on the same track return 400. Do not generate first and then create a new track, otherwise the version change will cause the candidate to expire.

## Export Complete Song

```json
{
  "action":"render",
  "id":"PROJECT_ID",
  "version_id":"CURRENT_VERSION_ID",
  "title":"Final Mix",
  "lyrics":"[Instrumental]",
  "async":true,
  "callback_url":"https://example.com/webhooks/suno"
}
```

The server reads the authoritative project state of the specified version and assembles export parameters. When `start_beats` and `end_beats` are omitted, it exports by default from the earliest start point to the latest end point of all audible clips; muted tracks/clips do not participate, and only solo tracks are selected when solo tracks exist. An empty project or no valid audible tracks returns 400. The final-state result contains `render_id`, `audio_id`, `audio_url`, and duration. Projects are bound to the execution environment at creation and cannot be migrated across environments or automatically failed over.

> Only upload or process audio that you have legal rights to use. The Project API is currently in Beta; please persist the final audio URLs from important results.

## Polling and Failure Recovery

```json
{"action":"retrieve","id":"TASK_ID"}
```
Send the above request to `/suno/tasks`. A Projects task is considered successful when `finished_at` exists and `response.success=true`; `response.success=false` indicates failure. A submission returning HTTP 200 or a `task_id` only means it has been accepted, not that the audio is complete.

The same `Idempotency-Key` with the same request will return the original result (including failures), and will not automatically regenerate or charge repeatedly. To explicitly retry a failed operation, first query the original task to confirm the failure, then use a new key; do not resubmit while the original task is still processing or the result is uncertain.

Error categories include `studio_unavailable` / `studio_model_unavailable` (503, temporarily unable to process or model unavailable), `studio_model_unsupported` (400, the model does not support this operation), `studio_state_invalid` (400, the project state or export range is invalid), `too_many_requests` (429), `studio_audio_unavailable` (403, the referenced audio cannot be used for project export), and `content_rejected` (403). Preserve `trace_id` for troubleshooting.