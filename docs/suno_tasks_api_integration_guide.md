# Integration and Use of Sun
```json
{
  "_id": "66d2add5550a4144a5a88dfe",
  "id": "eae26f89-b64b-404d-a80c-761996660b1c",
  "api_id": "09a26295-5972-4392-9318-dcd9b218f90d",
  "application_id": "ab46a066-ad82-4180-b66b-49dedf8e8a2f",
  "created_at": 1725083093.077,
  "credential_id": "66614a7e-e624-494e-87a3-387099b8cbb4",
  "request": {
    "action": "generate",
    "prompt": "A song for Christmas"
  },
  "trace_id": "e13d385a-077e-4376-be01-3465b61ca0fd",
  "user_id": "ad7afe47-cea9-4cda-980f-2ad8810e51cf",
  "response": {
    "success": true,
    "task_id": "eae26f89-b64b-404d-a80c-761996660b1c",
    "data": [
      {
        "id": "b8a4f691-4b14-4120-a7e1-a54a27a0e57e",
        "title": "Holiday Wishes",
        "image_url": "https://cdn2.suno.ai/image_b8a4f691-4b14-4120-a7e1-a54a27a0e57e.jpeg",
        "lyric": "[Verse]\nSnow is falling soft and white\nLights are twinkling oh so bright\nKids are laughing full of cheer\nChristmas time is finally here\n[Verse 2]\nBells are ringing in the night\nFireplace is warm with light\nCarols sung by the tree\nEveryone's together we agree\n[Chorus]\nHoliday wishes come true\nTime to share the joy with you\nSmiles and hugs for everyone\nMerry Christmas let's have fun\n[Verse 3]\nGifts are wrapped with loving care\nMagic's floating in the air\nCookies baking in the oven\nChristmas love to be given\n[Chorus]\nHoliday wishes come true\nTime to share the joy with you\nSmiles and hugs for everyone\nMerry Christmas let's have fun\n[Bridge]\nStars are shining in the sky\nHold your loved ones don't ask why\nHeart to heart we're all united\nOn this night we are delighted",
        "audio_url": "https://cdn1.suno.ai/b8a4f691-4b14-4120-a7e1-a54a27a0e57e.mp3",
        "video_url": "https://cdn1.suno.ai/b8a4f691-4b14-4120-a7e1-a54a27a0e57e.mp4",
        "created_at": "2024-08-31T05:44:54.806Z",
        "model": "chirp-v3.5",
        "prompt": "A song for Christmas",
        "style": "pop",
        "duration": 154.44
      },
      {
        "id": "1a3343b2-2c24-4584-a2a7-687e2f97f09e",
        "title": "Holiday Wishes",
        "image_url": "https://cdn2.suno.ai/image_1a3343b2-2c24-4584-a2a7-687e2f97f09e.jpeg",
        "lyric": "[Verse]\nSnow is falling soft and white\nLights are twinkling oh so bright\nKids are laughing full of cheer\nChristmas time is finally here\n[Verse 2]\nBells are ringing in the night\nFireplace is warm with light\nCarols sung by the tree\nEveryone's together we agree\n[Chorus]\nHoliday wishes come true\nTime to share the joy with you\nSmiles and hugs for everyone\nMerry Christmas let's have fun\n[Verse 3]\nGifts are wrapped with loving care\nMagic's floating in the air\nCookies baking in the oven\nChristmas love to be given\n[Chorus]\nHoliday wishes come true\nTime to share the joy with you\nSmiles and hugs for everyone\nMerry Christmas let's have fun\n[Bridge]\nStars are shining in the sky\nHold your loved ones don't ask why\nHeart to heart we're all united\nOn this night we are delighted",
        "audio_url": "https://cdn1.suno.ai/1a3343b2-2c24-4584-a2a7-687e2f97f09e.mp3",
        "video_url": "https://cdn1.suno.ai/1a3343b2-2c24-4584-a2a7-687e2f97f09e.mp4",
        "created_at": "2024-08-31T05:44:54.806Z",
        "model": "chirp-v3.5",
        "prompt": "A song for Christmas",
        "style": "pop",
        "duration": 147.16
      }
    ]
  }
}
```

The response contains multiple fields, the request field is the request body when initiating the task, while the response field is the response body returned after the task is completed. The field descriptions are as follows.

- `id`, the ID of the task that generated this song, used to uniquely identify this song generation task.
- `request`, the request information in the song task.
- `response`, the response information in the song task.

## Batch Query Operation

This is for querying the details of multiple task IDs, and unlike above, the action needs to be selected as retrieve_batch.

**Request Body** includes:

- `ids`: An array of uploaded task IDs.
- `action`: The operation method for the task.

Set as shown in the image below:

<p><img src="https://cdn.acedata.cloud/dqeknz.png" width="500" class="m-auto"></p>

### Code Example

It can be seen that various languages' code has been automatically generated on the right side, as shown in the image below:

<p><img src="https://cdn.acedata.cloud/1yk792.png" width="500" class="m-auto"></p>

Some code examples are as follows:

### Response Example

After a successful request, the API will return the specific detail information of all batch song tasks. For example:

```json {
  "items": [
    {
      "_id": "66d2add5550a4144a5a88dfe",
      "id": "eae26f89-b64b-404d-a80c-761996660b1c",
      "api_id": "09a26295-5972-4392-9318-dcd9b218f90d",
      "application_id": "ab46a066-ad82-4180-b66b-49dedf8e8a2f",
      "created_at": 1725083093.077,
      "credential_id": "66614a7e-e624-494e-87a3-387099b8cbb4",
      "request": {
        "action": "generate",
        "prompt": "A song for Christmas"
      },
      "trace_id": "e13d385a-077e-4376-be01-3465b61ca0fd",
      "user_id": "ad7afe47-cea9-4cda-980f-2ad8810e51cf",
      "response": {
        "success": true,
        "task_id": "eae26f89-b64b-404d-a80c-761996660b1c",
        "data":
[
          {
            "id": "b8a4f691-4b14-4120-a7e1-a54a27a0e57e",
            "title": "Holiday Wishes",
            "image_url": "https://cdn2.suno.ai/image_b8a4f691-4b14-4120-a7e1-a54a27a0e57e.jpeg",
            "lyric": "[Verse]\nSnow is falling soft and white\nLights are twinkling oh so bright\nKids are laughing full of cheer\nChristmas time is finally here\n[Verse 2]\nBells are ringing in the night\nFireplace is warm with light\nCarols sung by the tree\nEveryone's together we agree\n[Chorus]\nHoliday wishes come true\nTime to share the joy with you\nSmiles and hugs for everyone\nMerry Christmas let's have fun\n[Verse 3]\nGifts are wrapped with loving care\nMagic's floating in the air\nCookies baking in the oven\nChristmas love to be given\n[Chorus]\nHoliday wishes come true\nTime to share the joy with you\nSmiles and hugs for everyone\nMerry Christmas let's have fun\n[Bridge]\nStars are shining in the sky\nHold your loved ones don't ask why\nHeart to heart we're all united\nOn this night we are delighted",
            "audio_url": "https://cdn1.suno.ai/b8a4f691-4b14-4120-a7e1-a54a27a0e57e.mp3",
            "video_url": "https://cdn1.suno.ai/b8a4f691-4b14-4120-a7e1-a54a27a0e57e.mp4",
            "created_at": "2024-08-31T05:44:54.806Z",
            "model": "chirp-v3.5",
            "prompt": "A song for Christmas",
            "style": "pop",
            "duration": 154.44
          }, {
            "id": "1a3343b2-2c24-4584-a2a7-687e2f97f09e",
            "title": "Holiday Wishes",
            "image_url": "https://cdn2.suno.ai/image_1a3343b2-2c24-4584-a2a7-687e2f97f09e.jpeg",
            "lyric": "[Verse]\nSnow is falling soft and white\nLights are twinkling oh so bright\nKids are laughing full of cheer\nChristmas time is finally here\n[Verse 2]\nBells are ringing in the night\nFireplace is warm with light\nCarols sung by the tree\nEveryone's together we agree\n[Chorus]\nHoliday wishes come true\nTime to share the joy with you\nSmiles and hugs for everyone\nMerry Christmas let's have fun\n[Verse 3]\nGifts are wrapped with loving care\nMagic's floating in the air\nCookies baking in the oven\nChristmas love to be given\n[Chorus]\nHoliday wishes come true\nTime to share the joy with you\nSmiles and hugs for everyone\nMerry Christmas let's have fun\n[Bridge]\nStars are shining in the sky\nHold your loved ones don't ask why\nHeart to heart we're all united\nOn this night we are delighted",
            "audio_url": "https://cdn1.suno.ai/1a3343b2-2c24-4584-a2a7-687e2f97f09e.mp3",
            "video_url": "https://cdn1.suno.ai/1a3343b2-2c24-4584-a2a7-687e2f97f09e.mp4",
            "created_at": "2024-08-31T05:44:54.806Z",
            "model": "chirp-v3.5",
            "prompt": "A song for Christmas",
            "style": "pop",
            "duration": 147.16
          }
        ]
      }
    }, {
      "_id": "66d2b03c550a4144a5a8d93d",
      "id": "0d3ed03b-912b-4f7d-941b-8441323cb77b",
      "api_id": "09a26295-5972-4392-9318-dcd9b218f90d",
      "application_id": "ab46a066-ad82-4180-b66b-49dedf8e8a2f",
      "created_at": 1725083708.53,
      "credential_id": "66614a7e-e624-494e-87a3-387099b8cbb4",
      "request": {
        "action": "generate",
        "prompt": "la la la"
      },
      "trace_id": "29ebb919-1126-4156-86cc-4ad899432a8c",
      "user_id": "ad7afe47-cea9-4cda-980f-2ad8810e51cf",
      "response": {
        "success": true,
        "task_id": "0d3ed03b-912b-4f7d-941b-8441323cb77b",
        "data": [
          {
            "id": "b4f498b2-e86f-4172-926a-39da9df84dd3",
            "title": "La La La",
            "image_url": "https://cdn2.suno.ai/image_b4f498b2-e86f-4172-926a-39da9df84dd3.jpeg",
            "lyric": "[Verse]\nI wake up every morning\nLooking out the window\nSunshine shining bright\nBeginning of a new day\n[Verse 2]\nThe birds sing joyfully\nI dance in the garden\nSurrounded by beautiful flowers\nEvery moment here is mine\n[Chorus]\nLa la la la la la\nSing with me\nDon't stop\nLa la la la la la\nRejoice enjoying life\n[Verse 3]\nThe sea is blue and vast\nWaves crash sweetly\nWe walk on beaches\nRegardless of the weather\n[Bridge]\nSeize every hour\nListen to my songs\nFeel free\nHappy\nDance to the rhythm now\n[Chorus]\nLa la la la la la\nSing with me\nDon't stop\nLa la la la la la\nRejoice enjoying life",
            "audio_url": "https://cdn1.suno.ai/b4f498b2-e86f-4172-926a-39da9df84dd3.mp3",
            "video_url": "https://cdn1.suno.ai/b4f498b2-e86f-4172-926a-39da9df84dd3.mp4",
            "created_at": "2024-08-31T05:55:09.345Z",
            "model": "chirp-v3.5",
            "prompt": "la la la",
            "style": "pop",
            "duration": 154.32
          },
{
            "id": "8b44fdf1-3b88-47ac-a351-7c4b4de60549",
            "title": "La La La",
            "image_url": "https://cdn2.suno.ai/image_8b44fdf1-3b88-47ac-a351-7c4b4de60549.jpeg",
            "lyric": "[Verse]\nI wake up every morning\nLooking through the window\nSunshine shining bright\nBeginning of a new day\n[Verse 2]\nThe birds sing joyfully\nI dance in the garden\nSurrounded by beautiful flowers\nEvery moment here is mine\n[Chorus]\nLa la la la la la\nSing with me\nDon't stop\nLa la la la la la\nRejoice enjoying life\n[Verse 3]\nThe sea blue and vast\nWaves crash sweetly\nWe walk on beaches\nRegardless of the weather\n[Bridge]\nCapture every hour\nHear my songs\nFeel free\nHappy\nDance to the rhythm now\n[Chorus]\nLa la la la la la\nSing with me\nDon't stop\nLa la la la la la\nRejoice enjoying life",
            "audio_url": "https://cdn1.suno.ai/8b44fdf1-3b88-47ac-a351-7c4b4de60549.mp3",
            "video_url": "https://cdn1.suno.ai/8b44fdf1-3b88-47ac-a351-7c4b4de60549.mp4",
            "created_at": "2024-08-31T05:55:09.345Z",
            "model": "chirp-v3.5",
            "prompt": "la la la",
            "style": "pop",
            "duration": 177.36
          }
        ]
      }
    }
  ],
  "count": 2
}
```
 

The returned result contains multiple fields, where items include the specific details of the batch song tasks, and each song task's specific information is the same as the fields above.

- `items`, all specific details of the batch song tasks. It is an array, and each element of the array has the same format as the result of querying a single task above.
- `count`, the number of song tasks in this batch query.

#### CURL

```bash
curl -X POST 'https://api.acedata.cloud/suno/tasks' \
-H 'accept: application/json' \
-H 'authorization: Bearer {token}' \
-H 'content-type: application/json' \
-d '{
  "ids": ["eae26f89-b64b-404d-a80c-761996660b1c","0d3ed03b-912b-4f7d-941b-8441323cb77b"],
  "action": "retrieve_batch"
}'
```

#### Python

```python
import requests

url = "https://api.acedata.cloud/suno/tasks"

headers = {
    "accept": "application/json",
    "authorization": "Bearer {token}",
    "content-type": "application/json"
}

payload = {
    "ids": ["eae26f89-b64b-404d-a80c-761996660b1c","0d3ed03b-912b-4f7d-941b-8441323cb77b"],
    "action": "retrieve_batch"
}

response = requests.post(url, json=payload, headers=headers)
print(response.text)
```

## Error Handling

When calling the API, if an error occurs, the API will return the corresponding error code and message. For example:

- `400 token_mismatched`: Bad request, possibly due to missing or invalid parameters.
- `400 api_not_implemented`: Bad request, possibly due to missing or invalid parameters.
- `401 invalid_token`: Unauthorized, invalid or missing authorization token.
- `429 too_many_requests`: Too many requests, you have exceeded the rate limit.
- `500 api_error`: Internal server error, something went wrong on the server.

### Error Response Example

```json
{
  "success": false,
  "error": {
    "code": "api_error",
    "message": "fetch failed"
  },
  "trace_id": "2cf86e86-22a4-46e1-ac2f-032c0f2a4e89"
}
```

## Conclusion

Through this document, you have learned how to use the Suno Tasks API to query the specific details of single or batch song tasks. We hope this document helps you better integrate and use the API. If you have any questions, please feel free to contact our technical support team.