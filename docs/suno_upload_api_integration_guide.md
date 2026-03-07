# Suno Upload Reference Audio API Integration Instructions

SUNO allows us to upload reference audio for secondary creation. This document explains the integration method of the related API.

This API has only one input parameter, which is `audio_url`, a publicly accessible CDN address that supports the mp3 suffix.

Here, the `audio_url` we input is `https://cdn.acedata.cloud/suno_demo.mp3`, which is a publicly accessible CDN address.

```bash
curl -X POST 'https://api.acedata.cloud/suno/upload' \
-H 'accept: application/json' \
-H 'authorization: Bearer {token}' \
-H 'content-type: application/json' \
-d '{
  "audio_url": "https://cdn.acedata.cloud/suno_demo.mp3"
}'
```

The result is as follows:

```
{
    "success": true,
    "task_id": "058f8450-3df4-4f8b-8b64-ebc2e59ed3bc",
    "data": {
        "audio_id": "00135f7d-cda1-4d70-b007-779f07143586",
        "lyric": "[Intro]\nHa-ha-ha-ha-ha-ha\n[Verse 1]\nCandy skies are dripping blue\nStuck in world of chewed up glue\nThe sun's a lollipop melting slow\nDripped in sugar on the ground below\nOh-oh\n[Chorus]\nIt's a bubblegum catastrophe\nSticky mess can't set it free\nPop it once it multiplies\nCandy chaos in disguise\nIt's a bubblegum catastrophe\nSticky mess can't set it free\nPop it once it multiplies\nCandy chaos in disguise\nHa-ha-ha-ha-ha hey\nHa-ha-ha-ha-ha hey\nHa-ha-ha-ha-ha hey\nHa-ha-ha-ha-ha hey\nCandy chaos in disguise\n[Verse 2]\nJellybean mountains crumble fast\nRainbows made of soda blast\nEvery step's a gummy bear trap\nMy sugar rush is taking a nap\nOh-oh\n[Bridge]\nChew it up (ha-ha-ha-ha)\nSpit it out (ha-ha-ha-ha)\nRound and round (ha-ha-ha-ha)\nWithout a doubt (ha-ha-ha-ha)\n[Chorus]\nIt's a bubblegum catastrophe\nSticky mess can't set it free\nPop it once it multiplies\nCandy chaos in disguise\nIt's a bubblegum catastrophe\nSticky mess can't set it free\nPop it once it multiplies\nCandy chaos in disguise\nHa-ha-ha-ha-ha hey\nHa-ha-ha-ha-ha hey\nHa-ha-ha-ha-ha hey\nHa-ha-ha-ha-ha hey\n[Outro]\nCotton candy clouds collapse\nChocolate rivers running laps\nEverywhere's a sugar flood\nMy shoes are drowning caramel\nHa-ha-ha-ha-ha hey\nHa-ha-ha-ha-ha hey\nHa-ha-ha-ha-ha hey\nHa-ha-ha-ha-ha hey\nIt's a bubblegum catastrophe\nSticky mess can't set it free\nPop it once it multiplies\nCandy chaos in disguise\nIt's a bubblegum catastrophe\nSticky mess can't set it free\nPop it once it multiplies\nCandy chaos in disguise",
        "style": "Upbeat bubblegum pop track with a high-energy electronic production style. The song features a bright, processed female vocal with a youthful and energetic tone, often layered with harmonies and occasional pitch-shifted ad-libs. The instrumentation is dominated by bouncy, staccato synthesizer chords, a driving four-on-the-floor electronic drum beat with crisp claps on the backbeat, and a prominent, melodic bassline. The tempo is approximately 128 BPM in a major key, utilizing a standard pop chord progression of I-V-vi-IV. Production elements include heavy use of sidechain compression, vocal chops, and shimmering sound effects that contribute to a sugary, hyper-pop aesthetic. The structure follows a verse-chorus-verse-chorus-bridge-chorus format with a high-energy build-up leading into the explosive, hook-driven choruses.",
        "image_url": "https://cdn2.suno.ai/image_00135f7d-cda1-4d70-b007-779f07143586.jpeg",
        "image_large_url": "https://cdn2.suno.ai/image_large_00135f7d-cda1-4d70-b007-779f07143586.jpeg",
        "audio_url": "https://cdn1.suno.ai/00135f7d-cda1-4d70-b007-779f07143586.mp3",
        "title": "up-d6c3970d-6db1-41e3-b966-90539c93678a",
        "duration": 131.16
    }
}
```

As can be seen, the `audio_id` field in `data` is the song ID after uploading.

With the song ID, we can use the [Suno Audios Generation API](https://platform.acedata.cloud/documents/4da95d9d-7722-4a72-857d-bf6be86036e9) to generate custom songs. For example, by passing `action` as `upload_extend` and `audio_id` as the returned song ID, we can generate a new song based on the reference audio.