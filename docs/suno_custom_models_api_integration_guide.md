# Suno Custom Models API Integration Guide

Create a reusable custom music model from 6–24 audio files that you own or are authorized to use. The Beta API uses one endpoint with action-based operations:

```text
POST https://api.acedata.cloud/suno/custom-models
```

## Create a model

Send a stable `Idempotency-Key` header and reuse it if the request must be retried.

```bash
curl -X POST 'https://api.acedata.cloud/suno/custom-models' \
  -H 'Authorization: Bearer YOUR_API_TOKEN' \
  -H 'Content-Type: application/json' \
  -H 'Idempotency-Key: album-sound-v1' \
  -d '{
    "action": "create",
    "name": "My Album Sound",
    "audio_urls": [
      "https://cdn.example.com/track-01.mp3",
      "https://cdn.example.com/track-02.mp3",
      "https://cdn.example.com/track-03.mp3",
      "https://cdn.example.com/track-04.mp3",
      "https://cdn.example.com/track-05.mp3",
      "https://cdn.example.com/track-06.mp3"
    ]
  }'
```

The request returns immediately with a platform model `id`, task ID, and `queued` status. Only a successful model creation is charged.

## Retrieve status

```bash
curl -X POST 'https://api.acedata.cloud/suno/custom-models' \
  -H 'Authorization: Bearer YOUR_API_TOKEN' \
  -H 'Content-Type: application/json' \
  -d '{"action":"retrieve","id":"CUSTOM_MODEL_ID"}'
```

A model can be used only when its status is `ready`. Models are scoped to the Suno application that created them; rotating an API credential does not change ownership.

List models with pagination:

```json
{
  "action": "retrieve_batch",
  "status": "ready",
  "limit": 20,
  "offset": 0
}
```

## Generate music

```json
{
  "action": "generate",
  "id": "CUSTOM_MODEL_ID",
  "lyric": "[Verse]\nOriginal lyrics here",
  "style": "warm indie pop",
  "title": "New Song",
  "async": true
}
```

Generation returns a task ID and follows the standard Suno async result flow. An accepted async task is not terminal success; poll it until `response.success` is true or `response.error` is present. Custom-model generation never silently falls back to another model.

## Archive a model

```json
{
  "action": "delete",
  "id": "CUSTOM_MODEL_ID"
}
```

The Beta `delete` action archives the platform resource and prevents further generation. A response with `capacity_released: false` does not promise that model capacity was released.

## Important constraints

- Submit 6–24 distinct, publicly accessible HTTPS audio URLs.
- Use only audio for which you have the required model-training and generation rights.
- A Suno application has at most three custom-model slots.
- Do not treat `uploading` or `training` as success; wait for `ready`.
- Keep the returned platform model ID private to your application.
