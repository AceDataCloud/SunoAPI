# Suno Reference Audio Upload API Integration Guide

SUNO allows us to upload reference audio for secondary creation. This document explains how to integrate the related APIs.

A standard upload only requires `audio_url`, which is a publicly accessible audio CDN URL. `mode` defaults to `standard`, so no changes are required for existing calls. A successful standard upload consumes **0.06 Credits**; failed uploads are not charged.

The `audio_url` entered here is `https://cdn.acedata.cloud/suno_demo.mp3`, which is a publicly accessible CDN URL.

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
        "image_url": "https://cdn.acedata.cloud/e724d7f13d.png?example=image-001",
        "image_large_url": "https://cdn.acedata.cloud/e724d7f13d.png?example=image-002",
        "audio_url": "https://cdn.acedata.cloud/assets/examples/fish/5ade0339-5f11-487e-aacc-06a908271706-8e3fcb0e5547.mp3",
        "title": "up-d6c3970d-6db1-41e3-b966-90539c93678a",
        "duration": 131.16
    }
}
```

As you can see, `data` is always an object, and `audio_id` is the uploaded song ID. Analysis results such as `lyric`, `style`, `duration`, title, and media URLs are optional fields, depending on the returned content.

After obtaining the song ID, you can use the [Suno Audios Generation API](https://platform.acedata.cloud/documents/suno-audios) to call operations that require `audio_id`, such as `upload_extend`, `upload_cover`, or segment sampling. To use the Inspo inspiration creation feature to create new music based on 1 to 4 complete reference audio tracks, directly call `action=inspo` and pass the list of original public audio URLs; the service will automatically complete uploading and analysis, with no need for the client to assemble audio metadata.

## Enhanced Upload Mode

> `audio_url` is the input URL and will be directly passed to the audio processing workflow. It will not be pre-transferred by the final-state media persistence service. Please ensure that it is publicly accessible during task processing.

When standard upload cannot process audio that you own or are authorized to use, you can set `mode` to `enhanced`. This mode must also provide a `name` between 1 and 100 characters, and use a publicly accessible HTTPS `audio_url`.

Enhanced upload always uses asynchronous processing and typically takes 2 minutes or longer. Successful processing consumes **1.87 Credits**; failed processing is not charged.

```bash
curl -X POST 'https://api.acedata.cloud/suno/upload' \
  -H 'authorization: Bearer {token}' \
  -H 'content-type: application/json' \
  -d '{
    "audio_url": "https://cdn.acedata.cloud/suno_demo.mp3",
    "mode": "enhanced",
    "name": "My Song"
  }'
```

The API will immediately return `task_id` and `trace_id`. Use the [Suno Tasks API](https://platform.acedata.cloud/documents/suno-tasks) to query the task, and after success, read the uploaded audio ID from `response.data.audio_id`. You can also provide an HTTPS `callback_url` to receive the final state.

The `audio_id` obtained through enhanced upload can be used for Cover, Samples, and Mashup. Instrumental and MIDI extraction, full-track separation, and vocal/instrumental separation may still be restricted by the account that owns the audio; operations not listed are not guaranteed to support cross-account use. The shorter the audio, the higher the processing success rate usually is.