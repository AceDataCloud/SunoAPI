# Suno Mashup Lyrics Generation API Integration Instructions

If you want to use the lyrics of two songs to generate a mashup song, you can first use this API to generate the corresponding lyrics. The API is the [Suno MashupLyrics Generation API](https://platform.acedata.cloud/documents/851f9405-5f19-405a-8dbd-df4bd88e05a2).

The main input parameters for this API are `lyrics_a` and `lyrics_b`, with an example as follows:

![](https://cdn.acedata.cloud/g9n3t6.png)

Click to run, and the result is as follows:

```
{
  "success": true,
  "task_id": "80aa3cd3-ca87-4ca3-82d2-1830e3d8f53a",
  "data": {
    "text": "Sambuy come back  \nBluespawn, greenspawn are making you a spawn  \n\nSambuy come  \nSambuy come back  \nBluespawn, greenspawn are making you a spawn  \n\nSambuy come  \nSambuy come back  \nBluespawn, greenspawn are making you a spawn  \n\nSambuy come  \nSambuy come back  \nSambuy come, Sambuy come back  \nBluespawn, greenspawn are making you a spawn  \n\nSambuy come  \nSambuy come back  \nBluespawn, greenspawn are making you a spawn  \nSambuy come back",
    "title": "Lyrics Mashup",
    "tags": [],
    "status": "complete"
  }
}
```

As you can see, the `text` field in `data` contains the lyrics information.

With the lyrics in hand, we can then use the [Suno Audios Generation API](https://platform.acedata.cloud/documents/4da95d9d-7722-4a72-857d-bf6be86036e9) to generate a custom song.