# Suno Upload Reference Audio API Integration Instructions

SUNO allows us to upload reference audio for secondary creation. This document explains the integration method of the related API.

This API has only one input parameter, which is `audio_url`, a publicly accessible CDN address that supports the mp3 suffix.

Here, the `audio_url` we input is `https://cdn.acedata.cloud/suno_demo.mp3`, which is a publicly accessible CDN address.

```bash
curl -X POST 'https://api.acedata.cloud/suno/upload' \
-H 'accept: application/json' \
-H 'authorization: Bearer {token}' \
-H 'content-type: application/json' \
-d '{
  "audio_url": "https://cdn.acedata.cloud/suno_demo.mp3"
}'
```

The result is as follows:

```
{
  "success": true,
  "task_id": "57e8ce3a-39cb-41a2-802f-e70a324f4d0a",
  "data": {
    "audio_id": "eae26f89-b64b-404d-a80c-761996660b1c"
  }
}
```

As can be seen, the `audio_id` field in `data` is the ID of the uploaded song.

With the song ID, we can use the [Suno Audios Generation API](https://platform.acedata.cloud/documents/4da95d9d-7722-4a72-857d-bf6be86036e9) to generate custom songs. For example, by passing `upload_extend` as the `action` and the returned song ID as `audio_id`, we can generate a new song based on the reference audio.