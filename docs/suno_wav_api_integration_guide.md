# Suno Wav API Integration Guide

SUNO allows us to obtain music files in WAV format. This document explains the integration method for the related API.

The core input parameter for this API is `audio_id`, which is the official generated song ID; optionally, it also supports a `callback_url` for asynchronous callbacks.

Here, the `audio_id` we input is `4e43116a-bf09-472c-8e1c-655eabf02682`.

```python
import requests

url = "https://api.acedata.cloud/suno/wav"

headers = {
    "accept": "application/json",
    "authorization": "Bearer aa287fa4cc54401087a9fab3f99630af",
    "content-type": "application/json"
}

payload = {
    "audio_id": "4e43116a-bf09-472c-8e1c-655eabf02682"
}

response = requests.post(url, json=payload, headers=headers)
print(response.text)
```

The result is as follows:

```json
{
  "success": true,
  "task_id": "6a5a2099-d6d3-4930-9709-a30ac5dc7de5",
  "trace_id": "3fa70e81-6bb7-4ca8-b718-dd16a4eda7e8",
  "data": [
    {
      "file_url": "https://platform.cdn.acedata.cloud/suno/6a5a2099-d6d3-4930-9709-a30ac5dc7de5.wav"
    }
  ]
}
```

As you can see, the `file_url` field in `data` is the WAV format music file obtained. It is a publicly accessible CDN address.

> **Regarding the persistence and validity period of the WAV link**
>
> The WAV files on the upstream Suno CDN (`https://cdn1.suno.ai/{audio_id}.wav`) are only retained for a few days and will be recycled afterward, returning a 403 when accessed.
> To avoid link expiration, this API automatically transfers the upstream WAV file to our own CDN (`https://platform.cdn.acedata.cloud/suno/{task_id}.wav`) before returning. The returned `file_url` is the stable address after transfer and will not immediately become invalid due to upstream CDN expiration.
> The transferred link is valid for 30 days. After 30 days, the file will be regularly cleaned up. It is recommended to download it promptly and properly save it to your own storage.
> In rare cases of transfer failure, it will fall back to the original upstream URL, maintaining the historical behavior.