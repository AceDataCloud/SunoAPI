# Suno Vox API Integration Guide

SUNO allows us to create the new Persona-v2-vox version: singer style. Unlike the old version, it is necessary to first obtain `vox_audio_id`. This document explains the integration method for creating the new Persona-v2-vox.

First, you need to use this API to obtain the `vox_audio_id` parameter value. This API can accept multiple input parameters, such as `audio_id`, `vocal_start`, and `vocal_end`. It refers to the song ID and the selected time range.

Here, the `audio_id` we enter is `42599b24-fb14-4cd3-a444-e15ffde3661b`.

```python
import requests

url = "https://api.acedata.cloud/suno/vox"

headers = {
    "accept": "application/json",
    "authorization": "Bearer {token}",
    "content-type": "application/json"
}

payload = {
    "audio_id": "42599b24-fb14-4cd3-a444-e15ffde3661b",
    "vocal_end": 30,
    "vocal_start": 20
}

response = requests.post(url, json=payload, headers=headers)
print(response.text)
```

The result is as follows:

```json
{
  "success": true,
  "task_id": "9d5ce870-18e3-4c17-a1d9-7ef5a07918e9",
  "trace_id": "c31b50cd-0dbe-4e53-a7a5-83965dc5ad6b",
  "data": {
    "id": "24f0827e-5847-4011-b9b7-fc0b62032b65",
    "source_clip_id": "42599b24-fb14-4cd3-a444-e15ffde3661b",
    "status": "complete",
    "vocal_audio_url": "https://cdn.acedata.cloud/assets/examples/fish/5ade0339-5f11-487e-aacc-06a908271706-8e3fcb0e5547.mp3",
    "vocal_end_s": 30,
    "vocal_start_s": 20,
    "wave_response": {
      "waveform_aggregates": [
        {
          "data": [
            [
              -4,
              4,
              -50,
              73,
              -2517,
              2887,

              294
            ],
            [
              -5,
              4,
              296
            ]
          ],
          "mip_map_level": 11
        },

        {
          "data": [
            [
              -19576,
              20406,
              -16717,
              16980,
              -18926,
              20807,
              -20029,
              20103,
              -16437,
              20899
            ],
            [
              -19578,
              20406,
              -16720,
              16980,
              -18825,
              20051,
              -20029,
              20103,
              -16453,
              20903
            ]
          ],
          "mip_map_level": 20
        }
      ]
    }
  }
}
```

As you can see, the `id` field in `data` is the `vox_audio_id` we need. Then, we go to the [Persona API](https://platform.acedata.cloud/documents/suno-persona) to create the new Persona-v2-vox: singer style. The specific input is as follows:

```python
import requests

url = "https://api.acedata.cloud/suno/persona"

headers = {
    "accept": "application/json",
    "authorization": "Bearer {token}",
    "content-type": "application/json"
}

payload = {
    "name": "test",
    "audio_id": "42599b24-fb14-4cd3-a444-e15ffde3661b",
    "vocal_end": 30,
    "vocal_start": 20,
    "vox_audio_id": "24f0827e-5847-4011-b9b7-fc0b62032b65"
}

response = requests.post(url, json=payload, headers=headers)
print(response.text)
```

After calling it, the following result is obtained:

```json
{
  "success": true,
  "task_id": "e04b06a1-ff61-48e2-9fcc-15284bd18481",
  "data": {
    "persona_id": "49bef16d-6a09-49d1-8c24-a81663698b98"
  }
}
```

Then, we can use the `persona_id` value above to create with the new Persona-v2-vox: singer style. The specific creation method is consistent with the [Suno Song Generation API Integration Guide](https://platform.acedata.cloud/documents/suno-audios-integration#%E8%87%AA%E5%AE%9A%E4%B9%89%E6%AD%8C%E6%89%8B%E9%A3%8E%E6%A0%BC%E7%94%9F%E6%88%90%E5%8A%9F%E8%83%BD). Finally, we can use the Suno Vox API to create songs with the new Persona-v2-vox: singer style.