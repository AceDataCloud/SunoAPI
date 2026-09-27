# Suno MP3 URL API Integration Instructions

The Suno MP3 URL API generates a playable address ending with `.mp3` for existing music, suitable for scenarios where old download links are invalid, mobile playback is needed, or a public audio URL needs to be re-obtained.

The required parameter `audio_id` is the audio ID returned by the Suno audio generation interface. Each call will create an independent MP3 URL task, without modifying the original music generation task or changing the original audio ID.

## Synchronous Call

```python
import requests

response = requests.post(
    "https://api.acedata.cloud/suno/mp3",
    headers={
        "accept": "application/json",
        "authorization": "Bearer <YOUR_API_TOKEN>",
        "content-type": "application/json"
    },
    json={"audio_id": "ef1ec21e-1540-4eb6-8fa5-26cb8b90d28f"},
    timeout=240
)
response.raise_for_status()
result = response.json()
print(result["data"][0]["file_url"])
```

On success, `data[0].file_url` is the playable audio address. The interface will prioritize storing it at `https://cdn.acedata.cloud/suno/{audio_id}.mp3`; if persistence fails, it will return the currently available original media address.

## Asynchronous Call

For longer processing times, you can pass `async: true`:

```python
submission = requests.post(
    "https://api.acedata.cloud/suno/mp3",
    headers={"authorization": "Bearer <YOUR_API_TOKEN>"},
    json={
        "audio_id": "ef1ec21e-1540-4eb6-8fa5-26cb8b90d28f",
        "async": True
    }
).json()

export_task_id = submission["task_id"]
```

Then query `export_task_id` through `/suno/tasks`. You can also provide a `callback_url` to receive the final result after the task is completed. Synchronous responses, task queries, and callbacks use the same terminal data structure.

## Notes

- `audio_id` must come from a recognizable Suno audio.
- MP3 URL tasks are independent of the original music generation tasks.
- Persistence failures will not block results and will revert to the original media address; please download in a timely manner.
- It is recommended that the business side downloads the results promptly and saves them according to their data retention policy.