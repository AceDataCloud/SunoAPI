# Suno Voices API Integration Instructions

Suno allows you to create a custom voice persona from your own audio recording. The resulting `persona_id` can then be used with the [Suno Audios Generation API](https://platform.acedata.cloud/documents/4da95d9d-7722-4a72-857d-bf6be86036e9) to generate songs in that voice.

This API accepts three parameters:

- `audio_url`: A publicly accessible URL of the audio file (MP3 or WAV format, at least 10 seconds long, containing clear vocals from a single speaker without background noise or music).
- `name`: The name for the custom voice persona.
- `description`: A description of the custom voice persona.

```bash
curl -X POST 'https://api.acedata.cloud/suno/voices' \
-H 'accept: application/json' \
-H 'authorization: Bearer {token}' \
-H 'content-type: application/json' \
-d '{
  "audio_url": "https://cdn.acedata.cloud/suno_demo.mp3",
  "name": "My Voice",
  "description": "A clear male vocal recorded in a quiet room"
}'
```

The result is as follows:

```json
{
  "success": true,
  "task_id": "8e808558-f056-456f-91d6-b97fd94eb3be",
  "data": {
    "persona_id": "dde0be60-5280-4bd2-89a0-4020ddd3db52",
    "name": "My Voice",
    "is_public": false
  }
}
```

As can be seen, the `persona_id` field in `data` is the ID of the created voice persona. Voice personas created from uploaded audio are always private (`is_public: false`).

Pass the returned `persona_id` to the [Suno Audios Generation API](https://platform.acedata.cloud/documents/4da95d9d-7722-4a72-857d-bf6be86036e9) with `action: "generate"` to generate songs in that voice, or use it with `cover` / `upload_cover` for covers. No additional `vocal_gender` is needed; voice similarity still depends on the reference material and generated result.

## Cover a Song with a Private Voice

1. Create a voice through `/suno/voices` and retain `data.persona_id`.
2. Call `/suno/upload` with the original song's public `audio_url`, `mode: "standard"`, and that `persona_id`. This associates the uploaded song with the private voice. `persona_id` is not supported with enhanced upload mode.
3. After a successful upload, use its returned `data.audio_id` with the same `persona_id` in `/suno/audios`. This is a request template, not a recorded result:

   ```json
   {
     "action": "upload_cover",
     "model": "chirp-v6",
     "audio_id": "YOUR_VOICE_ASSOCIATED_AUDIO_ID",
     "persona_id": "YOUR_VOICE_PERSONA_ID",
     "custom": true,
     "instrumental": false,
     "lyric": "[Verse]\nWrite the lyrics to be sung",
     "async": true
   }
   ```

Voice creation, song upload, and cover generation must all use the same service channel. Do not reuse a song ID that was not associated with this private voice during upload; see the [upload guide](suno_upload_api_integration_guide.md#upload-a-song-for-a-private-voice-cover). A gender preference cannot replace `persona_id`.

## Python Voice Creation Example

The corresponding Python code:

```python
import requests

url = "https://api.acedata.cloud/suno/voices"

headers = {
    "accept": "application/json",
    "authorization": "Bearer {token}",
    "content-type": "application/json"
}

payload = {
    "audio_url": "https://cdn.acedata.cloud/suno_demo.mp3",
    "name": "My Voice",
    "description": "A clear male vocal recorded in a quiet room"
}

response = requests.post(url, json=payload, headers=headers)
print(response.text)
```
