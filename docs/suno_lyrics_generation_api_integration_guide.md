# Suno Lyrics Generation API Integration Instructions

If you want to customize song generation but don't want to write the lyrics yourself, you can use the lyrics generation API provided by AceDataCloud to generate lyrics through a prompt. The API is the [Suno Lyrics Generation API](https://platform.acedata.cloud/documents/suno-lyrics).

The main input parameter for this API is `prompt`, with an optional `model` (optional values are `default`, `remi-v1`, default is `default`). An example of the input is as follows:

![](https://cdn.acedata.cloud/p53wtj.png)

Here, the `prompt` we input is `A song about winter`, generating a song related to winter.

Click to run, and the result is as follows:

```json
{
  "success": true,
  "task_id": "2e26f7ff-0b82-4a60-bb9b-78db89f98b51",
  "data": [
    {
      "text": "[Verse]\nSnowflakes falling from the sky\nWinter's cold touch\nOh how it gets me high\nI bundle up in layers\nOh so cozy\nStepping out and feeling the frost on my nose\n\n[Chorus]\nOh\nWinter's cold touch\nIt's a season that I love so much\nSnowfall brings a feeling so divine\nWinter's cold touch\nIt's a magical time",
      "title": "Winter's Cold Touch",
      "status": "complete",
      "tags": ["dreamy, mellow, ballad"]
    },
    {
      "text": "[Verse]\nThe world is covered in a blanket of white\nIcicles hanging\nShimmering so bright\nThe chilly air fills my lungs with every breath\nWalking in the snow\nLeaving footprints behind\n\n[Chorus]\nWinter wonderland\nEverything is so bright\nWinter wonderland\nHold me through the night",
      "title": "Winter Wonderland",
      "status": "complete",
      "tags": ["dream pop, mellow, shoegaze"]
    }
  ],
  "started_at": 1780684179.15,
  "finished_at": 1780684186.583,
  "elapsed": 7.433
}
```

As you can see, `data` is an array that returns multiple lyric candidates each time, where the `text` field of each element is the lyric content, `title` is the title, and `tags` are the recommended genre tags.

With the lyrics in hand, we can then use the [Suno Audios Generation API](https://platform.acedata.cloud/documents/suno-audios) to generate custom songs.