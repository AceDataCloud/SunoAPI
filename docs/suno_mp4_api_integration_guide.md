# Suno MP4 API Integration Guide

SUNO allows us to obtain the officially generated MP4 link for generated music. This document explains the integration method for the related API.

This API has only one input parameter, which is `audio_id`, and it is the ID of the officially generated song.

Here, the `audio_id` we input is `275113ab-fe5c-4bca-a33c-0cca96b39fa6`.

```python
import requests

url = "https://api.acedata.cloud/suno/mp4"

headers = {
    "accept": "application/json",
    "authorization": "Bearer {token}",
    "content-type": "application/json"
}

payload = {
    "audio_id": "275113ab-fe5c-4bca-a33c-0cca96b39fa6"
}

response = requests.post(url, json=payload, headers=headers)
print(response.text)
```

The result is as follows:

```
{
  "success": true,
  "task_id": "03ae7cca-c3a2-40a0-98b2-8f33426af438",
  "trace_id": "848d8d5a-d6bb-4e16-bb29-768c22cf1b3b",
  "data": {
    "video_url": "https://cdn.acedata.cloud/assets/examples/gemini/04a043bd-6b23-4b4e-945c-ce48158c3eee-3a89912507c7.mp4"
  }
}
```

As you can see, the `video_url` field in `data` is the MP4 file link corresponding to the song.