# Suno Timing API Integration Guide

SUNO allows us to perform secondary creation on generated music, obtaining the lyrics and audio timeline. This document explains how to integrate with the related API.

This API has only one input parameter, which is `audio_id`, the official generated song ID.

Here, the `audio_id` we input is `ec13e502-d043-4eb2-92ee-e900c6da69d1`.

```python
import requests

url = "https://api.acedata.cloud/suno/timing"

headers = {
    "accept": "application/json",
    "authorization": "Bearer {token}",
    "content-type": "application/json"
}

payload = {
    "audio_id": "ec13e502-d043-4eb2-92ee-e900c6da69d1"
}

response = requests.post(url, json=payload, headers=headers)
print(response.text)
```

Excerpt of the result:

```
{
  "success": true,
  "task_id": "ccf72cca-1c82-4580-8575-bb141c7e8e48",
  "trace_id": "d8e0b7c3-6d24-4ed9-98ac-ffe683576a75",
  "data": {
    "aligned_words": [
      {
        "word": "[Verse]\nSnowflakes ",
        "success": true,
        "start_s": 2.63,
        "end_s": 3.43,
        "p_align": 0.531
      },
      {
        "word": "dance ",
        "success": true,
        "start_s": 3.43,
        "end_s": 3.91,
        "p_align": 0.911
      },
      {
        "word": "on ",
        "success": true,
        "start_s": 3.91,
        "end_s": 4.35,
        "p_align": 0.937
      },
      {
        "word": "rooftops ",
        "success": true,
        "start_s": 4.35,
        "end_s": 5.11,
        "p_align": 0.366
      },
      {
        "word": "high\n",
        "success": true,
        "start_s": 5.11,
        "end_s": 6.25,
        "p_align": 0.969
      },
      ...
    ],
    "waveform_data": [0.02138, 0.02193, 0.01806, 0.16597, 0.15168, 0.14243, ...],
    "hoot_cer": 0.35013262599469497,
    "is_streamed": false
  }
}
```

### Explanation of the aligned_words Field

As can be seen, `data.aligned_words` is an array of objects, each representing a word or phrase with timing information.

- `word`: The actual word or phrase in the lyrics
- `success`: Boolean indicating whether the alignment of this word was successful
- `start_s`: Start time of the word
- `end_s`: End time of the word
- `p_align`: Probability or confidence score of the alignment, ranging from 0 to 1