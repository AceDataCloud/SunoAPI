# Suno Music Generation API

This service has implemented the integration of Suno AI, which can be used to generate music, lyrics, and other content.

API home page: [Ace Data Cloud - Suno Music Generation](https://platform.acedata.cloud/services/f2b646d8-3cfd-46ef-969a-1ea9eebde329)

## Get Started


With the widespread application of AI, various AI programs have gradually become popular. AI has gradually penetrated all aspects of people's work and life. The industries involved in AI are also increasing, from the initial writing, to medical education, and now to music.

Suno is a professional high-quality AI song and music creation platform. Users only need to input simple text prompts to generate songs with vocals based on genre style and lyrics. This AI music generator is developed by team members from well-known tech companies such as Meta, TikTok, and Kensho, aiming to allow everyone to create wonderful music without any musical instruments.

Suno has recently upgraded its music generation model to version V4.5+, capable of generating 9-minute songs.

However, Suno does not officially provide an API. AceDataCloud offers a set of Suno APIs that simulate the official Suno interface, making it easy and quick to generate desired music.

### Application and Usage

To use the Suno Audios API, you can first visit the [Suno Audios Generation API](https://platform.acedata.cloud/documents/4da95d9d-7722-4a72-857d-bf6be86036e9) page and click the "Acquire" button to obtain the credentials needed for the request:

![](https://cdn.acedata.cloud/nyq0xz.png)

If you are not logged in or registered, you will be automatically redirected to the login page inviting you to register and log in. After logging in or registering, you will automatically return to the current page.

Upon the first application, there will be a free quota provided, allowing you to use the API for free.

### Basic Usage

To think of some songs, you can input any text, for example, if I want to generate a song about Christmas, I can input `a song for Christmas`, as shown in the image:

<p><img src="https://cdn.acedata.cloud/2kuuup.png" width="500" class="m-auto"></p>

Here we can see that we have set the Request Headers, including:

- `accept`: the format of the response result you want to receive, here filled in as `application/json`, which is JSON format.
- `authorization`: the key to call the API, which can be directly selected after application.

Additionally, the Request Body is set, including:

- `action`: the behavior of this music generation task, default is `generate`, mainly includes: `extend`, `upload_extend`, `cover`, `upload_cover`, `replace_section`, `replace_section`, `concat`, `stems`, `all_stems`.
- `prompt`: the prompt for Suno's official inspiration mode.
- `model`: the model for this music generation task, default is `chirp-v3-5`, mainly includes: `chirp-v3`, `chirp-v4`, `chirp-v3-5`, `chirp-v4-5`, `chirp-v4-5-plus`.
- `lyric`: the lyrics content for Suno's official custom mode.
- `custom`: whether to use the custom mode, default is: `false`.
- `instrumental`: the pure music option for Suno's official inspiration mode.
- `title`: the music title for Suno's official custom mode.
- `style`: the music style for Suno's official custom mode.
- `style_negative`: the excluded style for Suno's official custom mode.
- `audio_id`: the ID of the reference music.
- `persona_id`: the artist's song ID.
- `weirdness`: advanced parameter for weirdness.
- `continue_at`: the time in seconds to continue the existing audio. For example, 213.5 means continue to 3 minutes and 33.5 seconds.
- `style_influence`: advanced parameter for style influence.
- `replace_section_end`: the end time of the replacement section.
- `replace_section_start`: the start time of the replacement section.
- `callback_url`: the URL to receive the callback result.

The generated code is as follows:

<p><img src="https://cdn.acedata.cloud/1xehwl.png" width="500" class="m-auto"></p>

You can click the "Try" button to directly test the API, wait for 1-2 minutes, and the result is as follows:
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


## More

For more info, please check below APIs and integration documents

| API | Path | Integration Document |
| ---- | ---- | ------------ |
| [Suno Audios Generation API](http://platform.acedata.cloud/documents/4da95d9d-7722-4a72-857d-bf6be86036e9) | `/suno/audios` | [Suno Audios Generation API Integration Guide](http://platform.acedata.cloud/documents/d016ee3f-421b-4b6e-989a-8beba8701701) |
| [Suno Persona API](http://platform.acedata.cloud/documents/78bb6c62-6ce0-490f-a7df-e89d80ec0583) | `/suno/persona` | [Suno Persona API Integration Guide](http://platform.acedata.cloud/documents/a1ae233c-c52a-4a62-97dd-0db0c089da5a) |
| [Suno MP4 API](http://platform.acedata.cloud/documents/adf030f2-ac31-4342-bb65-afd9669272f9) | `/suno/mp4` | [Suno MP4 API Integration Guide](http://platform.acedata.cloud/documents/9dff19bb-3360-4578-8115-91c5efc130a3) |
| [$t(document_title_suno_timing_generation_api)](http://platform.acedata.cloud/documents/e8b5a84f-742f-4078-8b7d-a52a68aa253f) | `/suno/timing` | [Suno Timing API Integration Guide](http://platform.acedata.cloud/documents/149a2dd6-8af9-43f1-8994-0f4466b16c6f) |
| [$t(document_title_suno_wav_generation_api)](http://platform.acedata.cloud/documents/c55b2b82-416b-46d7-9854-4c3bf28a3cc5) | `/suno/wav` | [Suno Wav API Integration Guide](http://platform.acedata.cloud/documents/e48efa85-ed94-4ea8-8613-c16d734a3138) |
| [Suno Lyrics Generation API](http://platform.acedata.cloud/documents/514d82dc-f7ab-4638-9f21-8b9275916b08) | `/suno/lyrics` | [Suno Lyrics Generation API Integration Guide](http://platform.acedata.cloud/documents/f1c66741-a488-43ca-91fc-e53fbbda639a) |
| [Suno Tasks API](http://platform.acedata.cloud/documents/b0dd9823-0e01-4c75-af83-5a6e2e05bfed) | `/suno/tasks` | [Suno Tasks API Integration Guide](http://platform.acedata.cloud/documents/d3868342-7f11-4670-bd31-61a63663cb10) |
| [Suno Upload API](http://platform.acedata.cloud/documents/766db278-012c-43c4-9245-5f18d8dc4d82) | `/suno/upload` | [Suno Upload API Integration Guide](http://platform.acedata.cloud/documents/26092dda-23d9-4874-9916-e12db6fce3b5) |

Base URL: [https://api.acedata.cloud](https://api.acedata.cloud)

## Support 

If you meet any issue, check our from [support info](https://platform.acedata.cloud/support).