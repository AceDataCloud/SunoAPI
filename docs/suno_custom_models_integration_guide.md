# Suno Custom Music Model Integration Guide

Custom music models can learn consistent musical characteristics from 6 to 24 authorized audio tracks and use them for subsequent song creation. Creation is an asynchronous operation; it is recommended to use 24 audio tracks with consistent styles and clear audio quality for more stable results.

> You may only submit audio for which you have legal usage rights, or for which you have obtained authorization for model creation and subsequent generation. Do not upload unlicensed music or sound materials.

## Create a Model

Call `POST /suno/custom-models`, and set `action=create`:

```json
{
  "action": "create",
  "name": "My Indie Model",
  "audio_urls": [
    "https://cdn.example.com/song-01.mp3",
    "https://cdn.example.com/song-02.mp3",
    "https://cdn.example.com/song-03.mp3",
    "https://cdn.example.com/song-04.mp3",
    "https://cdn.example.com/song-05.mp3",
    "https://cdn.example.com/song-06.mp3"
  ],
  "callback_url": "https://example.com/webhooks/suno"
}
```

The API immediately returns the platform model ID and task ID. After creation is complete, the `status` in the callback or query result will change to `ready`. Only successful model creation will incur a charge of **10 Credits**; failed creation will not be charged.

## Query a Model

Query a single model:

```json
{
  "action": "retrieve",
  "id": "fa518f27-3fac-45cc-9b95-ae7ae0865b5e"
}
```

Query the current application's models with pagination:

```json
{
  "action": "retrieve_batch",
  "limit": 20,
  "offset": 0,
  "status": "ready"
}
```

All models belong to the Suno application that created them. API credential rotation does not change model ownership, and other applications cannot query or use the model.

## Generate Songs Using a Model

After the model status is `ready`, continue calling `POST /suno/custom-models`, and set `action=generate`:

```json
{
  "action": "generate",
  "id": "fa518f27-3fac-45cc-9b95-ae7ae0865b5e",
  "title": "Neon Rain",
  "lyric": "[Verse]\nCity lights are falling through the rain",
  "style": "indie rock, warm analog synth"
}
```

The `id` must be a custom music model under the current application with a status of `ready`. Requests will fail when the model is unavailable and will not automatically use another model. `persona_id` is mutually exclusive with custom music models; when submitted together, the API will return HTTP 400 before the request is sent to the generation service, and no charge will be incurred. To use Persona, use the `artist_consistency` or `artist_consistency_vox` operation of `/suno/audios` instead.

Successful song generation consumes **0.90 Credits**; failed generation will not be charged. Querying and archiving models are free.

## Archive a Model

```json
{
  "action": "delete",
  "id": "fa518f27-3fac-45cc-9b95-ae7ae0865b5e"
}
```

The current Beta version archives the model and prevents further use. `capacity_released=false` in the response indicates that archiving does not guarantee the release of model capacity. The archive operation can be called repeatedly and will not be charged repeatedly.