# Suno Song Generation API Integration Instructions

With the widespread application of AI, various AI programs have gradually become popular. AI has gradually penetrated all aspects of people's work and life. The industries involved in AI are also increasing, from the initial writing, to medical education, and now to music.

Suno is a professional high-quality AI song and music creation platform. Users only need to input simple text prompts to generate songs with vocals based on genre style and lyrics. This AI music generator is developed by team members from well-known tech companies such as Meta, TikTok, and Kensho, aiming to allow everyone to create wonderful music without any musical instruments.

The following is the progress of model updates:

| Version | model           | Launch Date  | prompt Limit | style Limit | Maximum Song Duration |
| ------- | --------------- | ------------ | ------------ | ----------- | --------------------- |
| v5     | chirp-v5        | 2025.09.23   | 5000         | 1000        | 8 minutes             |
| v4.5+  | chirp-v4-5-plus | 2025.07.17   | 5000         | 1000        | 8 minutes             |
| v4.5   | chirp-v4-5      | 2025.05.03   | 5000         | 1000        | 4 minutes             |
| v4     | chirp-v4        | 2024.12.17   | 3000         | 200         | 150 seconds           |
| v3.5   | chirp-v3-5      | ---          | 3000         | 200         | 120 seconds           |

Suno has recently upgraded its music generation model to version V5. To call the latest V5, simply change the model parameter to `chirp-v5`, which can generate songs up to 9 minutes long.

However, Suno does not officially provide an API. AceDataCloud offers a set of Suno APIs that simulate the official Suno interface, making it easy and quick to generate the desired music.

## Application and Usage

To use the Suno Audios API, you can first visit the [Suno Audios Generation API](https://platform.acedata.cloud/documents/4da95d9d-7722-4a72-857d-bf6be86036e9) page and click the "Acquire" button to obtain the credentials needed for requests:

![](https://cdn.acedata.cloud/nyq0xz.png)

If you are not logged in or registered, you will be automatically redirected to the login page inviting you to register and log in. After logging in or registering, you will be automatically returned to the current page.

There is a free quota available for first-time applicants, allowing you to use the API for free.

## Basic Usage

If you want to generate a song, you can input any text, for example, if I want to generate a song about Christmas, I can input `a song for Christmas`, as shown in the image:

<p><img src="https://cdn.acedata.cloud/2kuuup.png" width="500" class="m-auto"></p>

Here we can see that we have set the Request Headers, including:

- `accept`: the format of the response result you want to receive, here filled in as `application/json`, which means JSON format.
- `authorization`: the key to call the API, which can be directly selected after application.

Additionally, we set the Request Body, including:

- `action`: the action of this music generation task, default is `generate`, mainly includes: `extend`, `upload_extend`, `cover`, `upload_cover`, `replace_section`, `concat`, `stems`, `all_stems`, `remaster`.
- `prompt`: the prompt for Suno's official inspiration mode.
- `model`: the model for this music generation task, default is `chirp-v3-5`, mainly includes: `chirp-v3`, `chirp-v4`, `chirp-v3-5`, `chirp-v4-5`, `chirp-v4-5-plus`, `chirp-v5`.
- `lyric`: the lyrics content for Suno's official custom mode.
- `custom`: whether to use custom mode, default is: `false`.
- `instrumental`: the pure music option for Suno's official inspiration mode.
- `title`: the music title for Suno's official custom mode.
- `style`: the music style for Suno's official custom mode.
- `style_negative`: the excluded style for Suno's official custom mode.
- `audio_weight`: the proportion of the uploaded reference audio, range 0-1, the larger the more it relies on the reference audio.
- `audio_id`: the ID of the reference music.
- `overpainting_start`/`overpainting_end`: the start and end time in seconds for adding vocals to existing pure music.
- `underpainting_start`/`underpainting_end`: the start and end time in seconds for adding accompaniment to a cappella.
- `persona_id`: the artist's song ID.
- `continue_at`: the time in seconds to continue the existing audio. For example, 213.5 means continue to 3 minutes and 33.5 seconds.
- `style_influence`: advanced parameter for `style_influence`.
- `replace_section_end`: the final time for the replacement segment.
- `replace_section_start`: the starting time for the replacement segment.
- `vocal_gender`: controls the gender of the voice, female `f`, male `m`, effective for models 4.5 and above.
- `weirdness`: advanced parameter for `weirdness`.
- `lyric_prompt`: the prompt for generating lyrics, effective only when `custom` is `true` and `lyric` is not provided.
- `callback_url`: the URL for callback results.

The generated code is as follows:

<p><img src="https://cdn.acedata.cloud/1xehwl.png" width="500" class="m-auto"></p>

You can click the "Try" button to directly test the API, and after waiting for 1-2 minutes, the result is as follows:
```json
{
  "success": true,
  "task_id": "e72fb249-bd5b-4e2a-b20c-8a06fea5ac14",
  "trace_id": "7dbc5b6a-b2c0-4d85-9d39-fa8a8a785ccf",
  "data": [
    {
      "id": "b481b17a-bf50-4e10-8adc-4d5635050893",
      "title": "Under the Mistletoe",
      "image_url": "https://cdn2.suno.ai/image_b481b17a-bf50-4e10-8adc-4d5635050893.jpeg",
      "lyric": "[Verse]\nSnowflakes falling on the ground\nTwinkling lights all around\nThe scent of pine fills the air\nChristmas magic everywhere\n[Chorus]\nUnder the mistletoe tonight\nHearts aglow in the soft moonlight\nLaughter echoes\nSpirits bright\nIt’s Christmas time\nIt feels so right\n[Verse 2]\nStockings hung by the fire’s glow\nWarmth inside while the cold winds blow\nCookies baking\nSweet delight\nA season of joy shining bright\n[Chorus]\nUnder the mistletoe tonight\nHearts aglow in the soft moonlight\nLaughter echoes\nSpirits bright\nIt’s Christmas time\nIt feels so right\n[Bridge]\nCarols sung by candlelight\nStars above make the world feel tight\nPeace and love\nA season’s creed\nFilling hearts with all we need\n[Chorus]\nUnder the mistletoe tonight\nHearts aglow in the soft moonlight\nLaughter echoes\nSpirits bright\nIt’s Christmas time\nIt feels so right",
      "audio_url": "https://cdn1.suno.ai/b481b17a-bf50-4e10-8adc-4d5635050893.mp3",
      "video_url": "",
      "created_at": "2025-06-17T15:59:32.468Z",
      "model": "chirp-auk",
      "state": "succeeded",
      "prompt": "A song for Christmas",
      "style": "holiday, cheerful, male vocals",
      "duration": 154.92
    },
    {
      "id": "fbf22dab-5e2b-4e02-84c0-6d7605f14c3d",
      "title": "Under the Mistletoe",
      "image_url": "https://cdn2.suno.ai/image_fbf22dab-5e2b-4e02-84c0-6d7605f14c3d.jpeg",
      "lyric": "[Verse]\nSnowflakes falling on the ground\nTwinkling lights all around\nThe scent of pine fills the air\nChristmas magic everywhere\n[Chorus]\nUnder the mistletoe tonight\nHearts aglow in the soft moonlight\nLaughter echoes\nSpirits bright\nIt’s Christmas time\nIt feels so right\n[Verse 2]\nStockings hung by the fire’s glow\nWarmth inside while the cold winds blow\nCookies baking\nSweet delight\nA season of joy shining bright\n[Chorus]\nUnder the mistletoe tonight\nHearts aglow in the soft moonlight\nLaughter echoes\nSpirits bright\nIt’s Christmas time\nIt feels so right\n[Bridge]\nCarols sung by candlelight\nStars above make the world feel tight\nPeace and love\nA season’s creed\nFilling hearts with all we need\n[Chorus]\nUnder the mistletoe tonight\nHearts aglow in the soft moonlight\nLaughter echoes\nSpirits bright\nIt’s Christmas time\nIt feels so right",
      "audio_url": "https://cdn1.suno.ai/fbf22dab-5e2b-4e02-84c0-6d7605f14c3d.mp3",
      "video_url": "",
      "created_at": "2025-06-17T15:59:32.468Z",
      "model": "chirp-auk",
      "state": "succeeded",
      "prompt": "A song for Christmas",
      "style": "holiday, cheerful, male vocals",
      "duration": 158.48
    }
  ]
}
```

You can see that we have obtained the content of two songs, including the title, preview image, lyrics, audio, video, and other content.

The field descriptions are as follows:

- success: Indicates whether the generation was successful; if successful, it is `true`, otherwise it is `false`.
- data: A list that contains detailed information about the generated songs.
  - state: The song generation status, mainly includes four types, as follows:
    - succeeded: Generation successful
    - pending: In queue
    - running: In progress
    - error: Failed
  - id: Song ID
  - title: Title of the song
  - image_url: Cover image of the song
  - lyric: Lyrics of the song
  - audio_url: Audio file of the song, opening it will play an mp3 audio.
  - video_url: Video file of the song, opening it will play an mp4 video.
  - created_at: Creation time
  - model: The model used, generally the latest v3 model
  - style: Style

## Custom Generation

If you want to customize the generation of lyrics, you can input the lyrics:

At this time, the `lyric` field can accept content like the following:

```
[Verse]\nSnowflakes falling all around\nGlistening white\nCovering the ground\nChildren laughing\nFull of delight\nIn this winter wonderland tonight\nSanta's sleigh\nUp in the sky\nRudolph's nose shining bright\nOh my\nHear the jingle bells\nRinging so clear\nBringing joy and holiday cheer\n[Verse 2]\nRoasting chestnuts by the fire's glow\nChristmas lights\nThey twinkle and show\nFamilies gathering with love and cheer\nSpreading warmth to everyone near
```

> Note that the `\n` in the lyrics is a newline character. If you do not know how to generate lyrics, you can use the lyrics generation API provided by AceDataCloud to generate lyrics through a prompt. The API is [Suno Lyrics Generation API](https://platform.acedata.cloud/documents/514d82dc-f7ab-4638-9f21-8b9275916b08).

Next, we will customize the generation of songs based on the lyrics, title, and style, and you can specify the following content:

- lyric: Lyrics text
- custom: Set to `true`, indicating custom generation; this parameter defaults to false, indicating the use of prompt generation.
- title: Title of the song.
- style: Style of the song, optional.

An example of filling out is as follows:

<p><img src="https://cdn.acedata.cloud/qp3iba.png" width="500" class="m-auto"></p>

After filling it out, the generated code is as follows:

<p><img src="https://cdn.acedata.cloud/o5haei.png" width="500" class="m-auto"></p>

The corresponding code:

```shell
curl -X POST 'https://api.acedata.cloud/suno/audios' \
-H 'accept: application/json' \
-H 'authorization: Bearer {token}' \
-H 'content-type: application/json' \
-d '{
  "action": "generate",
  "prompt": "A song for Christmas",
  "model": "chirp-v4-5",
  "lyric": "[Verse]\\nSnowflakes falling all around\\nGlistening white\\nCovering the ground\\nChildren laughing\\nFull of delight\\nIn this winter wonderland tonight\\nSanta's sleigh\\nUp in the sky\\nRudolph's nose shining bright\\nOh my\\nHear the jingle bells\\nRinging so clear\\nBringing joy and holiday cheer\\n[Verse 2]\\nRoasting chestnuts by the fire's glow\\nChristmas lights\\nThey twinkle and show\\nFamilies gathering with love and cheer\\nSpreading warmth to everyone near",
  "custom": true
}'
```

Testing is allowed, and the generated effect is similar.

## Custom Singer Style Generation Function
If you want to generate a song using a singer's style, first generate a song using the basic usage mentioned above. Finally, you need to set this song to the singer's style, and then enter the [Suno Persona API](https://platform.acedata.cloud/documents/78bb6c62-6ce0-490f-a7df-e89d80ec0583) to generate a singer style id parameter `persona_id` based on the official generated music ID `audio_id`. The specific parameters are shown in the image below:

<p><img src="https://cdn.acedata.cloud/pmzo3l.png" width="500" class="m-auto"></p>

After filling it out, the automatically generated code is as follows:

<p><img src="https://cdn.acedata.cloud/a5g0nj.png" width="500" class="m-auto"></p>

Corresponding Python code:

```python
import requests

url = "https://api.acedata.cloud/suno/persona"

headers = {
    "accept": "application/json",
    "authorization": "Bearer {token}",
    "content-type": "application/json"
}

payload = {
    "audio_id": "97efc9f4-0e8d-4b3e-88df-14568fa1b11f",
    "name": "test"
}

response = requests.post(url, json=payload, headers=headers)
print(response.text)
```

Clicking run, you can find that a result will be obtained, as follows:

```json
{
  "success": true,
  "task_id": "7628b754-4fe7-4e79-bda4-806d0dd8bf6e",
  "data": {
    "persona_id": "e0d7319e-aa2a-44cb-b00a-916218d7cb0b"
  }
}
```

Using the above `audio_id` and `persona_id` as `97efc9f4-0e8d-4b3e-88df-14568fa1b11f` and `e0d7319e-aa2a-44cb-b00a-916218d7cb0b` for this example data. Then you can set the parameter `action` to `artist_consistency`, and input the ID of the song to continue generating, and the singer style ID, as shown in the example below:

<p><img src="https://cdn.acedata.cloud/fukijq.png" width="500" class="m-auto"></p>

After filling it out, the automatically generated code is as follows:

<p><img src="https://cdn.acedata.cloud/5uzk9d.png" width="500" class="m-auto"></p>

Corresponding Python code:

```python
import requests

url = "https://api.acedata.cloud/suno/audios"

headers = {
    "accept": "application/json",
    "authorization": "Bearer {token}",
    "content-type": "application/json"
}

payload = {
    "action": "artist_consistency",
    "prompt": "A song for Christmas",
    "model": "chirp-v4-5",
    "persona_id": "e0d7319e-aa2a-44cb-b00a-916218d7cb0b",
    "audio_id": "97efc9f4-0e8d-4b3e-88df-14568fa1b11f"
}

response = requests.post(url, json=payload, headers=headers)
print(response.text)
```

Clicking run, you can find that a result will be obtained, as follows:

```json
{
  "success": true,
  "task_id": "9b732b1a-bd67-48bc-95e4-90140e06836f",
  "trace_id": "30fcd88e-7687-4137-92d7-913b58115204",
  "data": [
    {
      "id": "727a36e2-8dce-4df7-99e5-14e44635c80f",
      "title": "",
      "image_url": "https://cdn2.suno.ai/image_727a36e2-8dce-4df7-99e5-14e44635c80f.jpeg",
      "lyric": "",
      "audio_url": "https://cdn1.suno.ai/727a36e2-8dce-4df7-99e5-14e44635c80f.mp3",
      "video_url": "",
      "created_at": "2025-06-17T16:27:33.979Z",
      "model": "chirp-auk",
      "state": "succeeded",
      "style": "",
      "duration": 244.4
    },
    {
      "id": "3b33301a-b17e-4b25-8842-09b46dab1a36",
      "title": "",
      "image_url": "https://cdn2.suno.ai/image_3b33301a-b17e-4b25-8842-09b46dab1a36.jpeg",
      "lyric": "",
      "audio_url": "https://cdn1.suno.ai/3b33301a-b17e-4b25-8842-09b46dab1a36.mp3",
      "video_url": "",
      "created_at": "2025-06-17T16:27:33.979Z",
      "model": "chirp-auk",
      "state": "succeeded",
      "style": "",
      "duration": 229.88
    }
  ]
}
```

It can be seen that the result content is consistent with the above, thus achieving the function of generating songs using the singer's style.

## Continue Generation Function

If you want to continue generating an already generated Suno song, you can set the parameter `action` to `extend`, and input the ID of the song to continue generating. The song ID can be obtained based on the basic usage, and from the above, you can see that the song ID is:

```
"id": "97efc9f4-0e8d-4b3e-88df-14568fa1b11f"
```

> Note that the `id` in the lyrics here is the ID of the generated song. If you do not know how to generate a song, you can refer to the basic usage above to generate a song.

If you want to continue generating a song that you uploaded, you can set the parameter `action` to `upload_extend`, and input the ID of the custom uploaded song to continue generating. The song ID can be obtained using the [Suno Upload Generation API](https://platform.acedata.cloud/documents/766db278-012c-43c4-9245-5f18d8dc4d82), as shown in the image below:

<p><img src="https://cdn.acedata.cloud/a0mn5e.png" width="500" class="m-auto"></p>

Next, we must fill in the lyrics and style to customize the generated song, specifying the following content:

- lyric: lyric text
- custom: set to `true`, representing custom generation. This parameter defaults to false, representing using `prompt` for generation.
- style: the style of the song, optional.
- continue_at: the time in seconds to continue the existing audio. For example, 213.5 means to continue to 3 minutes and 33.5 seconds.

The example for filling out is as follows:

<p><img src="https://cdn.acedata.cloud/zp9s42.png" width="500" class="m-auto"></p>

After filling it out, the automatically generated code is as follows:

<p><img src="https://cdn.acedata.cloud/wwpw78.png" width="500" class="m-auto"></p>

Corresponding Python code:
```python
import requests

url = "https://api.acedata.cloud/suno/audios"

headers = {
    "accept": "application/json",
    "authorization": "Bearer {token}",
    "content-type": "application/json"
}

payload = {
    "action": "extend",
    "prompt": "A song for Christmas",
    "model": "chirp-v4-5",
    "audio_id": "97efc9f4-0e8d-4b3e-88df-14568fa1b11f",
    "continue_at": 2,
    "lyric": "[Verse]\\nSnowflakes falling all around\\nGlistening white\\nCovering the ground\\nChildren laughing\\nFull of delight\\nIn this winter wonderland tonight\\nSanta's sleigh\\nUp in the sky\\nRudolph's nose shining bright\\nOh my\\nHear the jingle bells\\nRinging so clear\\nBringing joy and holiday cheer\\n[Verse 2]\\nRoasting chestnuts by the fire's glow\\nChristmas lights\\nThey twinkle and show\\nFamilies gathering with love and cheer\\nSpreading warmth to everyone near",
    "custom": True,
    "instrumental": False
}

response = requests.post(url, json=payload, headers=headers)
print(response.text)
```

Click to run, and you will find a result as follows:

```json
{
  "success": true,
  "task_id": "75b835d9-30d1-4641-8524-0aeedbdc9e1a",
  "trace_id": "44c41045-a2e1-4d19-aafc-7abd239d0d5c",
  "data": [
    {
      "id": "0a1e1b10-c36a-41c9-9bfb-b26d9d25db98",
      "title": "",
      "image_url": "https://cdn2.suno.ai/image_0a1e1b10-c36a-41c9-9bfb-b26d9d25db98.jpeg",
      "lyric": "[Verse]\\nSnowflakes falling all around\\nGlistening white\\nCovering the ground\\nChildren laughing\\nFull of delight\\nIn this winter wonderland tonight\\nSanta's sleigh\\nUp in the sky\\nRudolph's nose shining bright\\nOh my\\nHear the jingle bells\\nRinging so clear\\nBringing joy and holiday cheer\\n[Verse 2]\\nRoasting chestnuts by the fire's glow\\nChristmas lights\\nThey twinkle and show\\nFamilies gathering with love and cheer\\nSpreading warmth to everyone near",
      "audio_url": "https://cdn1.suno.ai/0a1e1b10-c36a-41c9-9bfb-b26d9d25db98.mp3",
      "video_url": "",
      "created_at": "2025-06-17T16:38:35.509Z",
      "model": "chirp-auk",
      "state": "succeeded",
      "style": "",
      "duration": 165.92
    },
    {
      "id": "4334c5b4-0a44-4b26-a8f6-66cc4dbb8fc3",
      "title": "",
      "image_url": "https://cdn2.suno.ai/image_4334c5b4-0a44-4b26-a8f6-66cc4dbb8fc3.jpeg",
      "lyric": "[Verse]\\nSnowflakes falling all around\\nGlistening white\\nCovering the ground\\nChildren laughing\\nFull of delight\\nIn this winter wonderland tonight\\nSanta's sleigh\\nUp in the sky\\nRudolph's nose shining bright\\nOh my\\nHear the jingle bells\\nRinging so clear\\nBringing joy and holiday cheer\\n[Verse 2]\\nRoasting chestnuts by the fire's glow\\nChristmas lights\\nThey twinkle and show\\nFamilies gathering with love and cheer\\nSpreading warmth to everyone near",
      "audio_url": "https://cdn1.suno.ai/4334c5b4-0a44-4b26-a8f6-66cc4dbb8fc3.mp3",
      "video_url": "",
      "created_at": "2025-06-17T16:38:35.509Z",
      "model": "chirp-auk",
      "state": "succeeded",
      "style": "",
      "duration": 158.84
    }
  ]
}
```

It can be seen that the result content is consistent with the above, thus achieving the function of continuing the song generation.

## Get the Complete Song

When continuing to generate a song based on the original song, the returned song does not contain the original song content. To obtain the complete song content, you need to use the concatenation function, and you can specify the following content:

- action: content is `concat`.
- audio_id: ID of the last segment.

For example, if the extended song ID is: 0a1e1b10-c36a-41c9-9bfb-b26d9d25db98, then you can set the parameters as follows:

```json
{
  "action": "concat",
  "audio_id": "0a1e1b10-c36a-41c9-9b26d9d25db98"
}
```

Other parameters remain unchanged, and the returned result will be a complete song, which is the concatenation result of all song segments, but the result will only be one song, as shown below:

```json
{
  "success": true,
  "task_id": "0f794915-8418-4124-93f5-b7eb3a417167",
  "trace_id": "62afcce0-e7e5-44b8-8c2e-4bba12a4f414",
  "data": [
    {
      "id": "0efec7e0-11bf-4313-9981-2c0e7218d7dd",
      "title": "",
      "image_url": "https://cdn2.suno.ai/image_0a1e1b10-c36a-41c9-9bfb-b26d9d25db98.jpeg",
      "lyric": "[Verse]\\nSnowflakes falling all around\\nGlistening white\\nCovering the ground\\nChildren laughing\\nFull of delight\\nIn this winter wonderland tonight\\nSanta's sleigh\\nUp in the sky\\nRudolph's nose shining bright\\nOh my\\nHear the jingle bells\\nRinging so clear\\nBringing joy and holiday cheer\\n[Verse 2]\\nRoasting chestnuts by the fire's glow\\nChristmas lights\\nThey twinkle and show\\nFamilies gathering with love and cheer\\nSpreading warmth to everyone near\n[Verse]\\nSnowflakes falling all around\\nGlistening white\\nCovering the ground\\nChildren laughing\\nFull of delight\\nIn this winter wonderland tonight\\nSanta's sleigh\\nUp in the sky\\nRudolph's nose shining bright\\nOh my\\nHear the jingle bells\\nRinging so clear\\nBringing joy and holiday cheer\\n[Verse 2]\\nRoasting chestnuts by the fire's glow\\nChristmas lights\\nThey twinkle and show\\nFamilies gathering with love and cheer\\nSpreading warmth to everyone near",
      "audio_url": "https://cdn1.suno.ai/0efec7e0-11bf-4313-9981-2c0e7218d7dd.mp3",
      "video_url": "",
      "created_at": "2025-06-17T16:43:06.718Z",
      "model": "chirp-auk",
      "state": "succeeded",
      "style": "",
      "duration": 167.91997916666668,
      "concat_history": [
        {
          "continue_at": 2,
          "id": "97efc9f4-0e8d-4b3e-88df-14568fa1b11f",
          "infill": false,
          "source": "web",
          "type": "gen"
        },
        {
          "id": "0a1e1b10-c36a-41c9-9bfb-b26d9d25db98"
        }
      ]
    }
  ]
}
```

## Music Version
When generating a song based on an existing song, the style of the returned song may not be appropriate. If you want to create a cover of the previously generated song (custom uploaded music is also supported), you need to use the music cover method, and you can specify the following content:

- action: The content is `cover`, and when it is a cover operation for custom uploaded music, the content must be specified as: `upload_cover`.
- audio_id: The ID of the previously generated song.

For example, if the ID of the previously generated song is: 0a1e1b10-c36a-41c9-9bfb-b26d9d25db98, then you can set the parameters as follows:

```json
{
  "action": "cover",
  "audio_id": "0a1e1b10-c36a-41c9-9bfb-b26d9d25db98",
  "prompt": "A song for Christmas",
  "model": "chirp-v4-5"
}
```

With other parameters unchanged, the returned result will be a cover song, which is the result of creating a cover of the previously generated song, as shown below:

```json
{
  "success": true,
  "task_id": "b9d43d06-2e0a-4b5e-9e0d-7dfab32e00ab",
  "trace_id": "6c5e567d-0fdc-4c44-9b36-4090d9a75ff5",
  "data": [
    {
      "id": "6988fa57-f810-41cf-afab-7838db2c77dc",
      "title": "",
      "image_url": "https://cdn2.suno.ai/image_6988fa57-f810-41cf-afab-7838db2c77dc.jpeg",
      "lyric": "",
      "audio_url": "https://cdn1.suno.ai/6988fa57-f810-41cf-afab-7838db2c77dc.mp3",
      "video_url": "",
      "created_at": "2025-06-17T16:44:13.007Z",
      "model": "chirp-auk",
      "state": "succeeded",
      "style": "",
      "duration": 182.4
    },
    {
      "id": "ce98b991-0258-4f05-8245-e43d4efa8fb8",
      "title": "",
      "image_url": "https://cdn2.suno.ai/image_ce98b991-0258-4f05-8245-e43d4efa8fb8.jpeg",
      "lyric": "",
      "audio_url": "https://cdn1.suno.ai/ce98b991-0258-4f05-8245-e43d4efa8fb8.mp3",
      "video_url": "",
      "created_at": "2025-06-17T16:44:13.007Z",
      "model": "chirp-auk",
      "state": "succeeded",
      "style": "",
      "duration": 179.72
    }
  ]
}
```

The generated result is similar to the above, completing the process of creating a cover of the previously generated song.

## Replace Section

When a song is generated and you need to perform a separate operation to replace a section of the song, you can specify the following content for replacing a certain section of the song:

- action: The content is `replace_section`.
- audio_id: The ID of the previously generated song.
- model: The song generation model,
- lyric: The complete lyrics after replacement (only needs to overlap with the prompt, not the complete lyrics),
- prompt: The part of the lyrics that needs to be replaced.
- style: The style of the song, optional.
- replace_section_start: The start time of the lyrics corresponding to `lyric` on the timeline.
- replace_section_end: The end time of the lyrics corresponding to `lyric` on the timeline.

For example, if the ID of the previously generated song is: ade7241b-0357-4a5e-9b3d-4ec4f4b3a0c0, then you can set the parameters as follows:

```json
{
  "action": "replace_section",
  "lyric": "[Chorus]\n新年快乐 人人欢快歌\n祝福洒满每一片角落\n新年快乐 心中花火多\n愿望成真生活似金色波\n[Verse 2]\n梅花绽放春意洋溢满地\n梅花绽放春意洋溢满地",
  "prompt": "梅花绽放春意洋溢满地\n梅花绽放春意洋溢满地",
  "replace_section_start": 28.94100580270793,
  "replace_section_end": 85.39410058027079,
  "model": "chirp-v4",
  "audio_id": "ade7241b-0357-4a5e-9b3d-4ec4f4b3a0c0",
  "custom": false,
  "instrumental": false
}
```

With other parameters unchanged, the returned result will be a song with the replaced section, which is the result of replacing a section of the previously generated song, as shown below:

```json
{
  "success": true,
  "task_id": "7a37c35d-7081-413d-908d-ab2d3f8139bf",
  "trace_id": "1ed92d6e-9a19-48f7-ab34-68c82c792303",
  "data": [
    {
      "id": "2a1467dc-51a4-4872-9ccc-ccd96e4fbbb6",
      "title": "新年快乐",
      "image_url": "https://cdn2.suno.ai/image_dc1b5edc-fbae-44a3-8962-d596dbd2b0d7.jpeg",
      "lyric": "[Chorus]\n新年快乐 人人欢快歌\n祝福洒满每一片角落\n新年快乐 心中花火多\n愿望成真生活似金色波\n[Verse 2]\n梅花绽放春意洋溢满地\n梅花绽放春意洋溢满地",
      "audio_url": "https://cdn1.suno.ai/2a1467dc-51a4-4872-9ccc-ccd96e4fbbb6.mp3",
      "video_url": "",
      "created_at": "2025-04-18T01:55:02.930Z",
      "model": "chirp-v4",
      "state": "succeeded",
      "style": "traditional influences, female vocals",
      "duration": 202.52,
      "concat_history": [
        {
          "id": "ade7241b-0357-4a5e-9b3d-4ec4f4b3a0c0",
          "type": "gen",
          "source": "ios",
          "infill_start_s": 28.94100580270793,
          "infill_end_s": 85.39410058027079,
          "infill_dur_s": 56.45309477756285,
          "infill_context_start_s": 0,
          "infill_context_end_s": 115.39410058027079,
          "include_future_s": 2,
          "include_history_s": 2,
          "infill": true,
          "infill_lyrics": "梅花绽放春意洋溢满地\n梅花绽放春意洋溢满地"
        },
        {
          "id": "dc1b5edc-fbae-44a3-8962-d596dbd2b0d7"
        }
      ]
    }
  ]
}
```
The generated result is similar to the previous text, thus completing the process of replacing segments of the originally generated song.

## Vocal and Instrument Separation

After generating the song, when a secondary creation is needed for separate operations of accompaniment and vocals, pure music accompaniment and clean vocals can be separated. The following content can be specified:

- action: content is `stems`.
- audio_id: the ID of the previously generated song.

For example, if the ID of the originally generated song is: ec13e502-d043-4eb2-92ee-e900c6da69d1, then the parameters can be set as follows:

```json
{
  "action": "stems",
  "audio_id": "ec13e502-d043-4eb2-92ee-e900c6da69d1"
}
```

With the above parameters, the result of vocal and instrumental separation can be obtained, as follows:

```json
{
  "success": true,
  "task_id": "4050affc-f8a6-4cba-a86c-bf201eed053d",
  "trace_id": "5107ee58-687d-422f-9195-fa0e82e1fcc8",
  "data": [
    {
      "id": "e3de0928-085a-42c4-b982-3b24738d1989",
      "title": "Deck the Sky - Vocals",
      "image_url": "https://cdn2.suno.ai/image_e3de0928-085a-42c4-b982-3b24738d1989.jpeg",
      "lyric": "[Verse]\nSnowflakes dance on rooftops high\nChildren's laughter fills the sky\nCarols ring from church bells loud\nHolidays a joyful crowd\n[Verse 2]\nCandy canes and cocoa warm\nWrapped up tight in our own storm\nStockings hung with dreams and cheer\nMagic growing every year\n[Chorus]\nDeck the sky with twinkling stars\nHoliday joy feels ours and ours\nSing the songs of love and light\nChristmas glows so pure and bright\n[Verse 3]\nFireside tales of long ago\nReindeer prance in icy glow\nEvergreen and tinsel’s gleam\nChristmas time a lovely dream\n[Bridge]\nHearts are full with friends and kin\nMistletoe for love to win\nGifts of love and hope we share\nChristmas spirit everywhere\n[Chorus]\nDeck the sky with twinkling stars\nHoliday joy feels ours and ours\nSing the songs of love and light\nChristmas glows so pure and bright",
      "audio_url": "https://cdn1.suno.ai/e3de0928-085a-42c4-b982-3b24738d1989.mp3",
      "video_url": "https://cdn1.suno.ai/e3de0928-085a-42c4-b982-3b24738d1989.mp4",
      "created_at": "2025-01-05T07:49:16.881Z",
      "model": "",
      "state": "succeeded",
      "style": "holiday, jolly",
      "duration": 174.16
    },
    {
      "id": "ad5d7c89-709c-4eb4-a5a6-72f9f5e57fdb",
      "title": "Deck the Sky - Instrumental",
      "image_url": "https://cdn2.suno.ai/image_ad5d7c89-709c-4eb4-a5a6-72f9f5e57fdb.jpeg",
      "lyric": "",
      "audio_url": "https://cdn1.suno.ai/ad5d7c89-709c-4eb4-a5a6-72f9f5e57fdb.mp3",
      "video_url": "https://cdn1.suno.ai/ad5d7c89-709c-4eb4-a5a6-72f9f5e57fdb.mp4",
      "created_at": "2025-01-05T07:49:16.892Z",
      "model": "",
      "state": "succeeded",
      "style": "holiday, jolly",
      "duration": 174.16
    }
  ]
}
```

The generated result is similar to the previous text, thus completing the process of vocal and instrumental separation of the originally generated song.

## Full Track Vocal and Instrument Separation

After generating the song, when a full track vocal and instrumental separation operation is needed, the following content can be specified:

- action: content is `all_stems`.
- audio_id: the ID of the previously generated song.

For example, if the ID of the originally generated song is: bdf23a5a-59f5-4103-b452-054a824a7f9f, then the parameters can be set as follows:

```json
{
  "action": "all_stems",
  "audio_id": "bdf23a5a-59f5-4103-b452-054a824a7f9f"
}
```

With the above parameters, the result of full track vocal and instrumental separation can be obtained, as follows:

```json
{
  "success": true,
  "task_id": "f4b16fb9-8478-4857-88c7-b9a1f0bb9518",
  "trace_id": "9c560ebd-4fc6-4bdb-988a-8890160a92fb",
  "data": [
    {
      "id": "f86ca64a-9519-4ea7-a592-52438e001412",
      "title": "安全之弦 (Vocals)",
      "image_url": "https://cdn2.suno.ai/image_f86ca64a-9519-4ea7-a592-52438e001412.jpeg",
      "lyric": "",
      "audio_url": "https://cdn1.suno.ai/f86ca64a-9519-4ea7-a592-52438e001412.mp3",
      "video_url": "",
      "created_at": "2025-06-11T02:40:30.770Z",
      "model": "chirp-ahi-stem-12-t1",
      "state": "succeeded",
      "duration": 154.92
    }, {
      "id": "99e649a7-a394-47b9-a915-d7f847285a36",
      "title": "安全之弦 (Backing Vocals)",
      "image_url": "https://cdn2.suno.ai/image_99e649a7-a394-47b9-a915-d7f847285a36.jpeg",
      "lyric": "",
      "audio_url": "https://cdn1.suno.ai/99e649a7-a394-47b9-a915-d7f847285a36.mp3",
      "video_url": "",
      "created_at": "2025-06-11T02:40:30.770Z",
      "model": "chirp-ahi-stem-12-t1",
      "state": "succeeded",
      "duration": 154.92
    }, {
      "id": "6d710bf7-809f-4fdc-bb63-b8cb3a456d42",
      "title": "安全之弦 (Drums)",
      "image_url": "https://cdn2.suno.ai/image_6d710bf7-809f-4fdc-bb63-b8cb3a456d42.jpeg",
      "lyric": "",
      "audio_url": "https://cdn1.suno.ai/6d710bf7-809f-4fdc-bb63-b8cb3a456d42.mp3",
      "video_url": "",
      "created_at": "2025-06-11T02:40:30.770Z",
      "model": "chirp-ahi-stem-12-t1",
      "state": "succeeded",
      "duration": 154.92
    },
{
      "id": "e05f07e3-7d80-4713-8e51-7f176c733543",
      "title": "The String of Safety (Bass)",
      "image_url": "https://cdn2.suno.ai/image_e05f07e3-7d80-4713-8e51-7f176c733543.jpeg",
      "lyric": "",
      "audio_url": "https://cdn1.suno.ai/e05f07e3-7d80-4713-8e51-7f176c733543.mp3",
      "video_url": "",
      "created_at": "2025-06-11T02:40:30.770Z",
      "model": "chirp-ahi-stem-12-t1",
      "state": "succeeded",
      "duration": 154.92
    }, {
      "id": "93fe7cd8-62fd-4739-b78e-142c7e0b8562",
      "title": "The String of Safety (Guitar)",
      "image_url": "https://cdn2.suno.ai/image_93fe7cd8-62fd-4739-b78e-142c7e0b8562.jpeg",
      "lyric": "",
      "audio_url": "https://cdn1.suno.ai/93fe7cd8-62fd-4739-b78e-142c7e0b8562.mp3",
      "video_url": "",
      "created_at": "2025-06-11T02:40:30.770Z",
      "model": "chirp-ahi-stem-12-t1",
      "state": "succeeded",
      "duration": 154.92
    }, {
      "id": "8367d71c-fdd3-441c-8ebe-70c33cca821b",
      "title": "The String of Safety (Keyboard)",
      "image_url": "https://cdn2.suno.ai/image_8367d71c-fdd3-441c-8ebe-70c33cca821b.jpeg",
      "lyric": "",
      "audio_url": "https://cdn1.suno.ai/8367d71c-fdd3-441c-8ebe-70c33cca821b.mp3",
      "video_url": "",
      "created_at": "2025-06-11T02:40:30.770Z",
      "model": "chirp-ahi-stem-12-t1",
      "state": "succeeded",
      "duration": 154.92
    }, {
      "id": "28c03590-731c-416e-8fd3-95cdb3d75043",
      "title": "The String of Safety (Percussion)",
      "image_url": "https://cdn2.suno.ai/image_28c03590-731c-416e-8fd3-95cdb3d75043.jpeg",
      "lyric": "",
      "audio_url": "https://cdn1.suno.ai/28c03590-731c-416e-8fd3-95cdb3d75043.mp3",
      "video_url": "",
      "created_at": "2025-06-11T02:40:30.770Z",
      "model": "chirp-ahi-stem-12-t1",
      "state": "succeeded",
      "duration": 154.92
    }, {
      "id": "3d4c1a28-4e1c-485a-8201-d21bb93aca2f",
      "title": "The String of Safety (Strings)",
      "image_url": "https://cdn2.suno.ai/image_3d4c1a28-4e1c-485a-8201-d21bb93aca2f.jpeg",
      "lyric": "",
      "audio_url": "https://cdn1.suno.ai/3d4c1a28-4e1c-485a-8201-d21bb93aca2f.mp3",
      "video_url": "",
      "created_at": "2025-06-11T02:40:30.770Z",
      "model": "chirp-ahi-stem-12-t1",
      "state": "succeeded",
      "duration": 154.92
    }, {
      "id": "b9db8ded-01ec-4e37-b8a5-64aab3a814c2",
      "title": "The String of Safety (Synth)",
      "image_url": "https://cdn2.suno.ai/image_b9db8ded-01ec-4e37-b8a5-64aab3a814c2.jpeg",
      "lyric": "",
      "audio_url": "https://cdn1.suno.ai/b9db8ded-01ec-4e37-b8a5-64aab3a814c2.mp3",
      "video_url": "",
      "created_at": "2025-06-11T02:40:30.770Z",
      "model": "chirp-ahi-stem-12-t1",
      "state": "succeeded",
      "duration": 154.92
    }, {
      "id": "10a5248e-32e6-42b9-8da1-678a8a392aef",
      "title": "The String of Safety (FX)",
      "image_url": "https://cdn2.suno.ai/image_10a5248e-32e6-42b9-8da1-678a8a392aef.jpeg",
      "lyric": "",
      "audio_url": "https://cdn1.suno.ai/10a5248e-32e6-42b9-8da1-678a8a392aef.mp3",
      "video_url": "",
      "created_at": "2025-06-11T02:40:30.770Z",
      "model": "chirp-ahi-stem-12-t1",
      "state": "succeeded",
      "duration": 154.92
    }, {
      "id": "2d272128-111f-4901-8f62-5ae1eb43095a",
      "title": "The String of Safety (Brass)",
      "image_url": "https://cdn2.suno.ai/image_2d272128-111f-4901-8f62-5ae1eb43095a.jpeg",
      "lyric": "",
      "audio_url": "https://cdn1.suno.ai/2d272128-111f-4901-8f62-5ae1eb43095a.mp3",
      "video_url": "",
      "created_at": "2025-06-11T02:40:30.770Z",
      "model": "chirp-ahi-stem-12-t1",
      "state": "succeeded",
      "duration": 154.92
    }, {
      "id": "4a7c19a5-f8d4-4e4a-add9-aa0bad9307cc",
      "title": "The String of Safety (Woodwinds)",
      "image_url": "https://cdn2.suno.ai/image_4a7c19a5-f8d4-4e4a-add9-aa0bad9307cc.jpeg",
      "lyric": "",
      "audio_url": "https://cdn1.suno.ai/4a7c19a5-f8d4-4e4a-add9-aa0bad9307cc.mp3",
      "video_url": "",
      "created_at": "2025-06-11T02:40:30.770Z",
      "model": "chirp-ahi-stem-12-t1",
      "state": "succeeded",
      "duration": 154.92
    }, {
      "id": "1ca774f9-3e75-48a6-941b-808875eadcd2",
      "title": "The String of Safety (Vocals)",
      "image_url": "https://cdn2.suno.ai/image_1ca774f9-3e75-48a6-941b-808875eadcd2.jpeg",
      "lyric": "",
      "audio_url": "https://cdn1.suno.ai/1ca774f9-3e75-48a6-941b-808875eadcd2.mp3",
      "video_url": "",
      "created_at": "2025-06-11T02:40:30.770Z",
      "model": "chirp-ahi-stem-12-t1",
      "state": "succeeded",
      "duration": 154.92
    },
{
      "id": "14c5ffc7-addf-4fee-afd2-4b8b3e7ee470",
      "title": "The String of Safety (Backing Vocals)",
      "image_url": "https://cdn2.suno.ai/image_14c5ffc7-addf-4fee-afd2-4b8b3e7ee470.jpeg",
      "lyric": "",
      "audio_url": "https://cdn1.suno.ai/14c5ffc7-addf-4fee-afd2-4b8b3e7ee470.mp3",
      "video_url": "",
      "created_at": "2025-06-11T02:40:30.771Z",
      "model": "chirp-ahi-stem-12-t1",
      "state": "succeeded",
      "duration": 154.92
    }, {
      "id": "9d044557-450d-48ab-90dc-8eaf6f1cdb6c",
      "title": "The String of Safety (Drums)",
      "image_url": "https://cdn2.suno.ai/image_9d044557-450d-48ab-90dc-8eaf6f1cdb6c.jpeg",
      "lyric": "",
      "audio_url": "https://cdn1.suno.ai/9d044557-450d-48ab-90dc-8eaf6f1cdb6c.mp3",
      "video_url": "",
      "created_at": "2025-06-11T02:40:30.771Z",
      "model": "chirp-ahi-stem-12-t1",
      "state": "succeeded",
      "duration": 154.92
    }, {
      "id": "efd052d0-c12f-47b3-8282-1f3ef7610e1f",
      "title": "The String of Safety (Bass)",
      "image_url": "https://cdn2.suno.ai/image_efd052d0-c12f-47b3-8282-1f3ef7610e1f.jpeg",
      "lyric": "",
      "audio_url": "https://cdn1.suno.ai/efd052d0-c12f-47b3-8282-1f3ef7610e1f.mp3",
      "video_url": "",
      "created_at": "2025-06-11T02:40:30.771Z",
      "model": "chirp-ahi-stem-12-t1",
      "state": "succeeded",
      "duration": 154.92
    }, {
      "id": "5775372b-292e-4420-96ef-60e57a60cc1f",
      "title": "The String of Safety (Guitar)",
      "image_url": "https://cdn2.suno.ai/image_5775372b-292e-4420-96ef-60e57a60cc1f.jpeg",
      "lyric": "",
      "audio_url": "https://cdn1.suno.ai/5775372b-292e-4420-96ef-60e57a60cc1f.mp3",
      "video_url": "",
      "created_at": "2025-06-11T02:40:30.771Z",
      "model": "chirp-ahi-stem-12-t1",
      "state": "succeeded",
      "duration": 154.92
    }, {
      "id": "dab3f220-19cd-408e-9b96-30ec18f5b049",
      "title": "The String of Safety (Keyboard)",
      "image_url": "https://cdn2.suno.ai/image_dab3f220-19cd-408e-9b96-30ec18f5b049.jpeg",
      "lyric": "",
      "audio_url": "https://cdn1.suno.ai/dab3f220-19cd-408e-9b96-30ec18f5b049.mp3",
      "video_url": "",
      "created_at": "2025-06-11T02:40:30.771Z",
      "model": "chirp-ahi-stem-12-t1",
      "state": "succeeded",
      "duration": 154.92
    }, {
      "id": "2d0cd6d4-af82-4bb5-86fe-d92bdb367157",
      "title": "The String of Safety (Percussion)",
      "image_url": "https://cdn2.suno.ai/image_2d0cd6d4-af82-4bb5-86fe-d92bdb367157.jpeg",
      "lyric": "",
      "audio_url": "https://cdn1.suno.ai/2d0cd6d4-af82-4bb5-86fe-d92bdb367157.mp3",
      "video_url": "",
      "created_at": "2025-06-11T02:40:30.771Z",
      "model": "chirp-ahi-stem-12-t1",
      "state": "succeeded",
      "duration": 154.92
    }, {
      "id": "f3191a1a-5e8d-4afe-b638-3add222d52cd",
      "title": "The String of Safety (Strings)",
      "image_url": "https://cdn2.suno.ai/image_f3191a1a-5e8d-4afe-b638-3add222d52cd.jpeg",
      "lyric": "",
      "audio_url": "https://cdn1.suno.ai/f3191a1a-5e8d-4afe-b638-3add222d52cd.mp3",
      "video_url": "",
      "created_at": "2025-06-11T02:40:30.771Z",
      "model": "chirp-ahi-stem-12-t1",
      "state": "succeeded",
      "duration": 154.92
    }, {
      "id": "a8834ea5-200b-4206-a812-9780ef336660",
      "title": "The String of Safety (Synth)",
      "image_url": "https://cdn2.suno.ai/image_a8834ea5-200b-4206-a812-9780ef336660.jpeg",
      "lyric": "",
      "audio_url": "https://cdn1.suno.ai/a8834ea5-200b-4206-a812-9780ef336660.mp3",
      "video_url": "",
      "created_at": "2025-06-11T02:40:30.771Z",
      "model": "chirp-ahi-stem-12-t1",
      "state": "succeeded",
      "duration": 154.92
    }, {
      "id": "f50d1a31-ef72-400a-b8ae-0367849d007d",
      "title": "The String of Safety (FX)",
      "image_url": "https://cdn2.suno.ai/image_f50d1a31-ef72-400a-b8ae-0367849d007d.jpeg",
      "lyric": "",
      "audio_url": "https://cdn1.suno.ai/f50d1a31-ef72-400a-b8ae-0367849d007d.mp3",
      "video_url": "",
      "created_at": "2025-06-11T02:40:30.771Z",
      "model": "chirp-ahi-stem-12-t1",
      "state": "succeeded",
      "duration": 154.92
    }, {
      "id": "cb581673-23cc-40d6-9f9b-0f76720f0d18",
      "title": "The String of Safety (Brass)",
      "image_url": "https://cdn2.suno.ai/image_cb581673-23cc-40d6-9f9b-0f76720f0d18.jpeg",
      "lyric": "",
      "audio_url": "https://cdn1.suno.ai/cb581673-23cc-40d6-9f9b-0f76720f0d18.mp3",
      "video_url": "",
      "created_at": "2025-06-11T02:40:30.771Z",
      "model": "chirp-ahi-stem-12-t1",
      "state": "succeeded",
      "duration": 154.92
    },
```json
{
      "id": "d91cfb52-f0a3-4546-bf8a-2ad14c3775a5",
      "title": "The String of Safety (Woodwinds)",
      "image_url": "https://cdn2.suno.ai/image_d91cfb52-f0a3-4546-bf8a-2ad14c3775a5.jpeg",
      "lyric": "",
      "audio_url": "https://cdn1.suno.ai/d91cfb52-f0a3-4546-bf8a-2ad14c3775a5.mp3",
      "video_url": "",
      "created_at": "2025-06-11T02:40:30.771Z",
      "model": "chirp-ahi-stem-12-t1",
      "state": "succeeded",
      "duration": 154.92
    }
  ]
}
```
 

The generated result is similar to the previous text, thus completing the process of separating the original generated song.

## Custom Advanced Parameters for Generation

The official allows the use of advanced parameters `weirdness` and `style_influence` in custom mode for generation, corresponding to the official examples as shown below:

<p><img src="https://cdn.acedata.cloud/ykr9lq.png" width="500" class="m-auto"></p>

The range of advanced parameters is between 0-1, and the specific parameters are shown in the image below:

<p><img src="https://cdn.acedata.cloud/i54sqm.png" width="500" class="m-auto"></p>

After filling in, the code is automatically generated as follows:

<p><img src="https://cdn.acedata.cloud/2dlbo6.png" width="500" class="m-auto"></p>

Corresponding Python code:

```python
import requests

url = "https://api.acedata.cloud/suno/audios"

headers = {
    "accept": "application/json",
    "authorization": "Bearer {token}",
    "content-type": "application/json"
}

payload = {
    "action": "generate",
    "model": "chirp-v4-5",
    "lyric": "Hello Hello Hello ",
    "custom": True,
    "weirdness": 0.4,
    "style_influence": 0.4
}

response = requests.post(url, json=payload, headers=headers)
print(response.text)
```

Clicking run, you can find that a result will be obtained, as follows:

```json
{
  "success": true,
  "task_id": "2f3aa682-e1a7-43a9-9fbb-ed0ce8668a4b",
  "trace_id": "07408194-7deb-4a52-a36d-9a9a13143b5f",
  "data": [
    {
      "id": "c66e2077-7580-43f2-9937-c67a8afcd8bd",
      "title": "",
      "image_url": "https://cdn2.suno.ai/image_c66e2077-7580-43f2-9937-c67a8afcd8bd.jpeg",
      "lyric": "Hello Hello Hello ",
      "audio_url": "https://cdn1.suno.ai/c66e2077-7580-43f2-9937-c67a8afcd8bd.mp3",
      "video_url": "",
      "created_at": "2025-07-10T12:54:35.199Z",
      "model": "chirp-auk",
      "state": "succeeded",
      "style": "",
      "duration": 187.92
    },
    {
      "id": "a922f97b-307c-4c4d-aae3-a47ba8202a10",
      "title": "",
      "image_url": "https://cdn2.suno.ai/image_a922f97b-307c-4c4d-aae3-a47ba8202a10.jpeg",
      "lyric": "Hello Hello Hello ",
      "audio_url": "https://cdn1.suno.ai/a922f97b-307c-4c4d-aae3-a47ba8202a10.mp3",
      "video_url": "",
      "created_at": "2025-07-10T12:54:35.199Z",
      "model": "chirp-auk",
      "state": "succeeded",
      "style": "",
      "duration": 229.64
    }
  ]
}
```

Thus, custom songs were generated using advanced parameters, and the results are similar to the previous text.

## Add Instrumental Function

In August 2025, Suno released the Add Instrumental function. First, you need to upload a song with only vocals and no accompaniment, allowing Suno to add music for you. You can first go to the [Suno Upload API](https://platform.acedata.cloud/documents/766db278-012c-43c4-9245-5f18d8dc4d82) to upload a song with only vocals, corresponding to the operations shown in the image below:

<p><img src="https://cdn.acedata.cloud/fxl914.png" width="500" class="m-auto"></p>

Then you need to record the `audio_id` after uploading, the specific result is shown in the image below:

<p><img src="https://cdn.acedata.cloud/47t6wj.png" width="500" class="m-auto"></p>

Finally, you get an `audio_id`: 92254cab-3372-4d9e-bce9-cdcfdbc39070, and then we need to fill in the following parameters:

- action: The content is `underpainting`.
- underpainting_start: The starting time for adding accompaniment to the uploaded song, the default value is 0.
- underpainting_end: The endpoint for adding accompaniment to the uploaded song, must be less than the total duration of the song.
- audio_id: The ID of the uploaded song with only vocals.
- style: The style of the accompaniment, preferably without lyrics since it is for accompaniment.

After filling in, the code is automatically generated as follows:

<p><img src="https://cdn.acedata.cloud/8x1ic6.png" width="500" class="m-auto"></p>

Corresponding Python code:

```python
import requests

url = "https://api.acedata.cloud/suno/audios"

headers = {
    "accept": "application/json",
    "authorization": "Bearer {token}",
    "content-type": "application/json"
}

payload = {
    "action": "underpainting",
    "model": "chirp-v4-5",
    "style": "Pop rap, uplifting, magnetic male vocals, piano, synth, electric guitar, driving bass, clear structure",
    "audio_id": "92254cab-3372-4d9e-bce9-cdcfdbc39070",
    "underpainting_end": 120
}

response = requests.post(url, json=payload, headers=headers)
print(response.text)
```

Clicking run, you can find that a result will be obtained, as follows:
```
```json
{
  "success": true,
  "task_id": "822d2e14-c535-4d48-a4e5-1b6ab00b04a7",
  "trace_id": "257eac2c-8e4f-44d0-8454-5e215111eefa",
  "data": [
    {
      "id": "2788cd21-bd84-422d-beb5-859c60fbf5b6",
      "title": "",
      "image_url": "https://cdn2.suno.ai/image_2788cd21-bd84-422d-beb5-859c60fbf5b6.jpeg",
      "lyric": "",
      "audio_url": "https://cdn1.suno.ai/2788cd21-bd84-422d-beb5-859c60fbf5b6.mp3",
      "video_url": "",
      "created_at": "2025-08-27T15:25:42.548Z",
      "model": "chirp-v4",
      "state": "succeeded",
      "style": "Pop rap, uplifting, magnetic male vocals, piano, synth, electric guitar, driving bass, clear structure",
      "duration": 10.16
    },
    {
      "id": "a4bb7220-e971-4cbf-a626-b86c648bcf55",
      "title": "",
      "image_url": "https://cdn2.suno.ai/image_a4bb7220-e971-4cbf-a626-b86c648bcf55.jpeg",
      "lyric": "",
      "audio_url": "https://cdn1.suno.ai/a4bb7220-e971-4cbf-a626-b86c648bcf55.mp3",
      "video_url": "",
      "created_at": "2025-08-27T15:25:42.548Z",
      "model": "chirp-v4",
      "state": "succeeded",
      "style": "Pop rap, uplifting, magnetic male vocals, piano, synth, electric guitar, driving bass, clear structure",
      "duration": 2.52
    }
  ]
}
```

This completes the operation of adding accompaniment to the uploaded a cappella song, with results similar to the above.

## Add Vocals Feature

In August 2025, Suno released the new Add Vocals feature. First, you need to upload a pure instrumental track for Suno to fill in the lyrics and provide vocal singing. You can start by uploading a cappella song without accompaniment to the [Suno Upload API](https://platform.acedata.cloud/documents/766db278-012c-43c4-9245-5f18d8dc4d82), as shown in the following operation:

<p><img src="https://cdn.acedata.cloud/fxl914.png" width="500" class="m-auto"></p>

Then you need to record the `audio_id` after uploading, with the specific result shown in the following image:

<p><img src="https://cdn.acedata.cloud/47t6wj.png" width="500" class="m-auto"></p>

Finally, you get an `audio_id`: 92254cab-3372-4d9e-bce9-cdcfdbc39070, and then you need to fill in the following parameters:

- action: The content is `overpainting`.
- overpainting_start: The starting time for adding vocals to the uploaded song, the default value is 0.
- overpainting_end: The endpoint for adding vocals to the uploaded song, must be less than the total duration of the song.
- audio_id: The ID of the uploaded a cappella song.
- custom: In this mode, you must use a custom mode to fill in the lyrics.
- lyric: The lyrics filled in the custom mode.
- style: The style of the accompaniment.

After filling in, the code is automatically generated as follows:

<p><img src="https://cdn.acedata.cloud/a4pbes.png" width="500" class="m-auto"></p>

Corresponding Python code:

```python
import requests

url = "https://api.acedata.cloud/suno/audios"

headers = {
    "accept": "application/json",
    "authorization": "Bearer {token}",
    "content-type": "application/json"
}

payload = {
    "action": "overpainting",
    "model": "chirp-v4-5",
    "lyric": "Yea your were the best I could get \\nBut I knew that it couldn’t last \\nStayed down since we were friends \\nHad to leave those thoughts in the past \\nMade like 40k just last week \\nOn top of the 20 with my babe\\ndon’t care for what niggas say",
    "custom": True,
    "audio_id": "92254cab-3372-4d9e-bce9-cdcfdbc39070",
    "overpainting_end": 120
}

response = requests.post(url, json=payload, headers=headers)
print(response.text)
```

Clicking run, you can find that you will get a result as follows:

```json
{
  "success": true,
  "task_id": "31bb250e-6614-49ec-ac85-631f224daeba",
  "trace_id": "efe8e7f3-9a65-4f13-a9f8-51e8478899df",
  "data": [
    {
      "id": "a597f945-64df-4722-a631-d436450832bd",
      "title": "",
      "image_url": "https://cdn2.suno.ai/image_a597f945-64df-4722-a631-d436450832bd.jpeg",
      "lyric": "Yea your were the best I could get \\nBut I knew that it couldn’t last \\nStayed down since we were friends \\nHad to leave those thoughts in the past \\nMade like 40k just last week \\nOn top of the 20 with my babe\\ndon’t care for what niggas say",
      "audio_url": "https://cdn1.suno.ai/a597f945-64df-4722-a631-d436450832bd.mp3",
      "video_url": "",
      "created_at": "2025-08-27T15:33:51.550Z",
      "model": "chirp-v4",
      "state": "succeeded",
      "style": "",
      "duration": 105.32
    },
    {
      "id": "b41a8b91-3d88-4ebd-a6cf-732764b24954",
      "title": "",
      "image_url": "https://cdn2.suno.ai/image_b41a8b91-3d88-4ebd-a6cf-732764b24954.jpeg",
      "lyric": "Yea your were the best I could get \\nBut I knew that it couldn’t last \\nStayed down since we were friends \\nHad to leave those thoughts in the past \\nMade like 40k just last week \\nOn top of the 20 with my babe\\ndon’t care for what niggas say",
      "audio_url": "https://cdn1.suno.ai/b41a8b91-3d88-4ebd-a6cf-732764b24954.mp3",
      "video_url": "",
      "created_at": "2025-08-27T15:33:51.550Z",
      "model": "chirp-v4",
      "state": "succeeded",
      "style": "",
      "duration": 148.16
    }
  ]
}
```

This completes the operation of adding vocals to the uploaded a cappella song, with results similar to the above.

## Remaster Feature

In December 2025, Suno released the new Remaster feature, which can regenerate songs but cannot cross accounts. Then you need to fill in the following parameters:

- action: The content is `remaster`.
- audio_id: The ID of the song to be regenerated.
- model: Only supports v4.5+, v5.
- variation_category: Only supported in versions above v5, and only has 3 values: high, normal, subtle.

After filling in, the code is automatically generated as follows:

<p><img src="https://cdn.acedata.cloud/7h4zmw.png" width="500" class="m-auto"></p>

Corresponding Python code:
```python
import requests

url = "https://api.acedata.cloud/suno/audios"

headers = {
    "accept": "application/json",
    "authorization": "Bearer {token}",
    "content-type": "application/json"
}

payload = {
    "action": "remaster",
    "variation_category": "high",
    "audio_id": "21fd46d4-45c3-4826-bec9-3f3df667902e"
}

response = requests.post(url, json=payload, headers=headers)
print(response.text)
```

Click to run, and you will find a result like the following:

```json
{
  "success": true,
  "task_id": "791ee74c-9363-4352-afe7-babb19b89899",
  "trace_id": "77acda57-c3d4-4e11-a506-4f50e0609916",
  "data": [
    {
      "id": "b0515cdf-9cb5-46cd-b0fe-10a239dc9274",
      "title": "Navidad en costura  (Remastered)",
      "image_url": "https://cdn2.suno.ai/image_b0515cdf-9cb5-46cd-b0fe-10a239dc9274.jpeg",
      "image_large_url": "https://cdn2.suno.ai/image_large_b0515cdf-9cb5-46cd-b0fe-10a239dc9274.jpeg",
      "lyric": "En Teror las clases siguen,\nni en Navidad hay parón;\ncose el grupo entre villancicos\ny un buen trocito de turrón.\nLa Popular abre sus puertas,\ny el taller suena mejor;\nhilo, aguja y canto alegre\nlo pasaremos mejor\nSeguimos en las costuras,\ncon música y diversión;\nlos alumnos comeremos\nGolosinas un montón ",
      "audio_url": "https://cdn1.suno.ai/b0515cdf-9cb5-46cd-b0fe-10a239dc9274.mp3",
      "video_url": "",
      "created_at": "2025-12-04T13:09:59.936Z",
      "model": "chirp-v4",
      "state": "succeeded",
      "style": "Villancico",
      "duration": 32.2
    },
    {
      "id": "06edab94-a4f9-4c0c-abac-a2e8a97c76a8",
      "title": "Navidad en costura  (Remastered)",
      "image_url": "https://cdn2.suno.ai/image_06edab94-a4f9-4c0c-abac-a2e8a97c76a8.jpeg",
      "image_large_url": "https://cdn2.suno.ai/image_large_06edab94-a4f9-4c0c-abac-a2e8a97c76a8.jpeg",
      "lyric": "En Teror las clases siguen,\nni en Navidad hay parón;\ncose el grupo entre villancicos\ny un buen trocito de turrón.\nLa Popular abre sus puertas,\ny el taller suena mejor;\nhilo, aguja y canto alegre\nlo pasaremos mejor\nSeguimos en las costuras,\ncon música y diversión;\nlos alumnos comeremos\nGolosinas un montón ",
      "audio_url": "https://cdn1.suno.ai/06edab94-a4f9-4c0c-abac-a2e8a97c76a8.mp3",
      "video_url": "",
      "created_at": "2025-12-04T13:09:59.936Z",
      "model": "chirp-v4",
      "state": "succeeded",
      "style": "Villancico",
      "duration": 32.2
    }
  ]
}
```

This completes the operation of regenerating the already generated song, with results similar to the above.

## Asynchronous Callback

Since the time for Suno to generate music is relatively long, approximately 1-2 minutes, if the API does not respond for a long time, the HTTP request will keep the connection open, leading to additional system resource consumption. Therefore, this API also provides support for asynchronous callbacks.

The overall process is: when the client initiates a request, an additional `callback_url` field is specified. After the client initiates the API request, the API will immediately return a result containing a `task_id` field, representing the current task ID. When the task is completed, the result of the generated music will be sent to the client's specified `callback_url` in the form of a POST JSON, which also includes the `task_id` field, allowing the task result to be associated by ID.

Let's understand how to operate specifically through an example.

First, the Webhook callback is a service that can receive HTTP requests, and developers should replace it with the URL of their own HTTP server. For demonstration purposes, we use a public Webhook sample site https://webhook.site/, where you can open the site to get a Webhook URL, as shown in the image:

![](https://cdn.acedata.cloud/fwfqin.png)

Copy this URL, and it can be used as a Webhook. The sample here is https://webhook.site/03e60575-3d96-4132-b681-b713d78116e2.

Next, we can set the `callback_url` field to the above Webhook URL and fill in the `prompt`, as shown in the image:

![](https://cdn.acedata.cloud/x8xql1.png)

Click to run, and you will immediately get a result like the following:

```
{
  "task_id": "44472ab8-783b-4054-b861-5bf14e462f60"
}
```

After a moment, we can observe the result of the generated song at https://webhook.site/03e60575-3d96-4132-b681-b713d78116e2, as shown in the image:

![](https://cdn.acedata.cloud/f9kosb.png)

The content is as follows:
```json
{
  "success": true,
  "task_id": "44472ab8-783b-4054-b861-5bf14e462f60",
  "data": [
    {
      "id": "da4324e5-84b2-484b-b0e9-dd261381c594",
      "title": "Winter Whispers",
      "image_url": "https://cdn1.suno.ai/image_da4324e5-84b2-484b-b0e9-dd261381c594.png",
      "lyric": "[Verse]\nSnow falling gently from the sky\nChildren giggling as they pass by\nFire crackling\nCozy and warm\nChristmas spirit begins to swarm\n[Verse 2]\nTwinkling lights\nA sight to behold\nStockings hung\nWaiting to be filled with gold\nGifts wrapped with love\nPiled high\nExcitement in the air\nYou can't deny\n[Chorus]\nWinter whispers in the wind\nJoy and love it brings\nLet's celebrate this season\nWith the ones we're missing",
      "audio_url": "https://cdn1.suno.ai/da4324e5-84b2-484b-b0e9-dd261381c594.mp3",
      "video_url": "https://cdn1.suno.ai/da4324e5-84b2-484b-b0e9-dd261381c594.mp4",
      "created_at": "2024-05-11T07:33:05.430Z",
      "model": "chirp-v3",
      "prompt": "A song for Christmas",
      "style": "pop"
    },
    {
      "id": "b878a87b-a0db-4046-8ccd-ecd2fb3d4372",
      "title": "Winter Whispers",
      "image_url": "https://cdn1.suno.ai/image_b878a87b-a0db-4046-8ccd-ecd2fb3d4372.png",
      "lyric": "[Verse]\nSnow falling gently from the sky\nChildren giggling as they pass by\nFire crackling\nCozy and warm\nChristmas spirit begins to swarm\n[Verse 2]\nTwinkling lights\nA sight to behold\nStockings hung\nWaiting to be filled with gold\nGifts wrapped with love\nPiled high\nExcitement in the air\nYou can't deny\n[Chorus]\nWinter whispers in the wind\nJoy and love it brings\nLet's celebrate this season\nWith the ones we're missing",
      "audio_url": "https://cdn1.suno.ai/b878a87b-a0db-4046-8ccd-ecd2fb3d4372.mp3",
      "video_url": "https://cdn1.suno.ai/b878a87b-a0db-4046-8ccd-ecd2fb3d4372.mp4",
      "created_at": "2024-05-11T07:33:05.430Z",
      "model": "chirp-v3",
      "prompt": "A song for Christmas",
      "style": "pop"
    }
  ]
}
```

You can see that the result contains a `task_id` field, and other fields are similar to the above text. This field can be used to associate tasks.

## Error Handling

If an error occurs, you will receive an error message similar to the following:

```json
{
  "success": false,
  "error": {
    "code": "forbidden",
    "message": "Song Description contained artist name: eminem"
  },
  "trace_id": "9bb7c2f4-3b7b-4965-b50a-f663874b1b6f",
  "task_id": "9bb3a2a6-c438-436d-a9f3-fa466abc077c"
}
```

Below is a list of HTTP Status Codes, `error.code`, and `error.message`:

| Status Code | `error.code`  | `error.message`                                                 |
| ----------- | ------------- | --------------------------------------------------------------- |
| 400         | `bad_request` | `The song id does not exist or has been taken offline.`         |
| 400         | `bad_request` | `Prompt too long.`                                              |
| 400         | `bad_request` | `Tags too long.`                                                |
| 400         | `bad_request` | `Uploaded audio matches existing work of art.`                  |
| 400         | `bad_request` | `instrumental must be a boolean`                                |
| 400         | `bad_request` | `Title too long.`                                               |
| 400         | `bad_request` | `Topic too long.`                                               |
| 400         | `bad_request` | `style must be less than or equal 120`                          |
| 400         | `bad_request` | `custom must be a boolean`                                      |
| 400         | `bad_request` | `audio_id is required when extend audio`                        |
| 400         | `bad_request` | `continue_at is required when extend audio`                     |
| 400         | `bad_request` | `continue_at must be a number greater than 0`                   |
| 400         | `bad_request` | `lyric is required when extend audio and instrumental is false` |
| 400         | `bad_request` | `prompt is required when generate audio`                        |
| 400         | `bad_request` | `lyric is required when generate custom audio`                  |
| 403         | `forbidden`   | `Prompt likely malformed`                                       |
| 403         | `forbidden`   | `Prompt likely copyrighted`                                     |
| 403         | `forbidden`   | `Prompt contained inappropriate material`                       |
| 403         | `forbidden`   | `Song Description flagged for moderation`                       |
| 403         | `forbidden`   | `Song Description contained artist name`                        |
| 403         | `forbidden`   | `Tags contained artist name`                                    |
| 403         | `forbidden`   | `Lyrics contained copyrighted material`                         |
| 403         | `forbidden`   | `Song Description contained producer tag`                       |
| 403         | `forbidden`   | `Generic openAI error`                                          |
| 403         | `forbidden`   | `Prompt flagged for moderation`                                 |
| 500         | `api_error`   | `Unable to generate lyrics from song description`               |
| 500         | `api_error`   | `job failed with unknown error`                                 |
| 500         | `api_error`   | `no available worker in system`                                 |
| 500         | `api_error`   | `service under maintenance, generation paused`                  |
| 504         | `timeout`     | `timeout while waiting for audio generation`                    |