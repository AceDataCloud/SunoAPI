# Suno Studio Project Integration Guide

The Suno Studio project API manages multi-track music projects through a single endpoint:

```http
POST /suno/projects
Authorization: Bearer YOUR_API_KEY
Content-Type: application/json
```

The `action` in the request determines the operation type. The Project primary key uniformly uses `id`; `version_id` represents the current project version, and all modification and export operations must submit the latest version to avoid concurrent overwrites.

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
| `render`           | Async | Export the saved version as a complete song   |

Asynchronous operations immediately return a `task_id`. Use the free `/suno/tasks` endpoint for polling, or pass `callback_url` to receive final-state results.

## Create and Retrieve

```json
{"action":"create","title":"My Studio Project"}
```

All modification operations should send a unique `Idempotency-Key` Header. After successful creation, `data.id` in the response is the Project ID. A newly created empty project may not have a `version_id` before its first save.

```json
{"action":"retrieve","id":"PROJECT_ID"}
```

The retrieve response contains the complete `state`. It is recommended to retrieve first, then modify and save based on the returned values; do not manually construct internal timing and track structures from scratch.

## Save Complete State

```json
{
  "action":"save",
  "id":"PROJECT_ID",
  "version_id":"CURRENT_VERSION_ID",
  "title":"Edited Project",
  "state":{"tracks":[],"timing":{}}
}
```

The first save of a newly created empty project may omit `version_id`; after the first save generates a version, subsequent saves must submit the latest value. If the version has changed, the API returns HTTP 409. In this case, `retrieve` again, merge the modifications, and then submit with a new idempotency key; do not blindly retry the old request.

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

After the upload is complete, the task result returns a candidate `audio_id`. Then add it to the project:

```json
{
  "action":"add_track",
  "id":"PROJECT_ID",
  "version_id":"CURRENT_VERSION_ID",
  "audio_id":"AUDIO_ID",
  "name":"Backing Vocals"
}
```

## Generate and Replace

`generate_track` generates track candidates for a project range; `replace_section` returns two local replacement candidates. Neither operation automatically selects an artistic result.

```json
{
  "action":"replace_section",
  "id":"PROJECT_ID",
  "version_id":"CURRENT_VERSION_ID",
  "source_audio_id":"AUDIO_ID",
  "start_seconds":35.12,
  "end_seconds":48.76,
  "model":"chirp-v6",
  "replacement_lyrics":"new lyric segment",
  "async":true
}
```

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

Candidates are bound to the project version at the time of generation. When the project has already changed, old candidates cannot be committed directly.

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

The server reads the authoritative project state of the specified version and assembles the export parameters. The final-state result contains `render_id`, `audio_id`, `audio_url`, and duration. Projects are bound to the execution environment at creation and cannot be migrated across environments or automatically fail over.

> Only upload or process audio for which you have legal usage rights. The project API is currently in Beta; please persist the final audio URL in important results.