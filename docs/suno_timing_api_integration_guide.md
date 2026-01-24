# Suno Timing API Integration Instructions

SUNO allows us to create secondary works from generated music, obtaining the lyrics and audio timeline of the music. This document explains the integration method for the relevant API.

This API has only one input parameter, which is `audio_id`, the official generated song ID.

The `audio_id` we input here is `ec13e502-d043-4eb2-92ee-e900c6da69d1`.

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

The result is as follows:

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
      }, {
        "word": "dance ",
        "success": true,
        "start_s": 3.43,
        "end_s": 3.91,
        "p_align": 0.911
      }, {
        "word": "on ",
        "success": true,
        "start_s": 3.91,
        "end_s": 4.35,
        "p_align": 0.937
      }, {
        "word": "rooftops ",
        "success": true,
        "start_s": 4.35,
        "end_s": 5.11,
        "p_align": 0.366
      }, {
        "word": "high\n",
        "success": true,
        "start_s": 5.11,
        "end_s": 6.25,
        "p_align": 0.969
      }, {
        "word": "Children's ",
        "success": true,
        "start_s": 6.57,
        "end_s": 8.34,
        "p_align": 0.655
      }, {
        "word": "laughter ",
        "success": true,
        "start_s": 8.34,
        "end_s": 9.18,
        "p_align": 0.453
      }, {
        "word": "fills ",
        "success": true,
        "start_s": 9.18,
        "end_s": 9.73,
        "p_align": 0.852
      }, {
        "word": "the ",
        "success": true,
        "start_s": 9.73,
        "end_s": 10.13,
        "p_align": 0.892
      }, {
        "word": "sky\n",
        "success": true,
        "start_s": 10.13,
        "end_s": 10.95,
        "p_align": 0.798
      }, {
        "word": "Carols ",
        "success": true,
        "start_s": 11.01,
        "end_s": 12.17,
        "p_align": 0.718
      }, {
        "word": "ring ",
        "success": true,
        "start_s": 12.17,
        "end_s": 12.61,
        "p_align": 0.975
      }, {
        "word": "from ",
        "success": true,
        "start_s": 12.61,
        "end_s": 13.09,
        "p_align": 0.824
      }, {
        "word": "church ",
        "success": true,
        "start_s": 13.09,
        "end_s": 13.52,
        "p_align": 0.952
      }, {
        "word": "bells ",
        "success": true,
        "start_s": 13.52,
        "end_s": 14.12,
        "p_align": 0.823
      }, {
        "word": "loud\n",
        "success": true,
        "start_s": 14.12,
        "end_s": 14.84,
        "p_align": 0.965
      }, {
        "word": "Holidays ",
        "success": true,
        "start_s": 15.03,
        "end_s": 16.52,
        "p_align": 0.643
      }, {
        "word": "a ",
        "success": true,
        "start_s": 16.52,
        "end_s": 16.95,
        "p_align": 0.98
      }, {
        "word": "joyful ",
        "success": true,
        "start_s": 16.95,
        "end_s": 17.59,
        "p_align": 0.985
      }, {
        "word": "crowd\n\n",
        "success": true,
        "start_s": 17.59,
        "end_s": 18.32,
        "p_align": 0.984
      }, {
        "word": "[Verse 2]\nCandy ",
        "success": true,
        "start_s": 18.96,
        "end_s": 19.79,
        "p_align": 0.959
      }, {
        "word": "canes ",
        "success": true,
        "start_s": 19.79,
        "end_s": 20.5,
        "p_align": 0.942
      }, {
        "word": "and ",
        "success": true,
        "start_s": 20.5,
        "end_s": 20.9,
        "p_align": 0.67
      }, {
        "word": "cocoa ",
        "success": true,
        "start_s": 20.9,
        "end_s": 21.7,
        "p_align": 0.541
      }, {
        "word": "warm\n",
        "success": true,
        "start_s": 21.7,
        "end_s": 22.58,
        "p_align": 0.641
      }, {
        "word": "Wrapped ",
        "success": true,
        "start_s": 22.75,
        "end_s": 23.58,
        "p_align": 0.026
      }, {
        "word": "up ",
        "success": true,
        "start_s": 23.58,
        "end_s": 23.98,
        "p_align": 0.157
      }, {
        "word": "tight ",
        "success": true,
        "start_s": 23.98,
        "end_s": 24.5,
        "p_align": 0.004
      }, {
        "word": "in ",
        "success": true,
        "start_s": 24.5,
        "end_s": 24.89,
        "p_align": 0.296
      }, {
        "word": "our ",
        "success": true,
        "start_s": 24.89,
        "end_s": 25.29,
        "p_align": 0.89
      }, {
        "word": "own ",
        "success": true,
        "start_s": 25.29,
        "end_s": 25.77,
        "p_align": 0.953
      }, {
        "word": "storm\n",
        "success": true,
        "start_s": 25.77,
        "end_s": 26.61,
        "p_align": 0.895
      }, {
        "word": "Stockings ",
        "success": true,
        "start_s": 26.77,
        "end_s": 27.81,
        "p_align": 0.488
      }, {
        "word": "hung ",
        "success": true,
        "start_s": 27.81,
        "end_s": 28.29,
        "p_align": 0.996
      }, {
        "word": "with ",
        "success": true,
        "start_s": 28.29,
        "end_s": 28.72,
        "p_align": 0.986
      },
{
        "word": "dreams ",
        "success": true,
        "start_s": 28.72,
        "end_s": 29.24,
        "p_align": 0.987
      }, {
        "word": "and ",
        "success": true,
        "start_s": 29.24,
        "end_s": 29.76,
        "p_align": 0.976
      }, {
        "word": "cheer\n",
        "success": true,
        "start_s": 29.76,
        "end_s": 30.6,
        "p_align": 0.969
      }, {
        "word": "Magic ",
        "success": true,
        "start_s": 30.67,
        "end_s": 31.52,
        "p_align": 0.986
      }, {
        "word": "growing ",
        "success": true,
        "start_s": 31.52,
        "end_s": 32.35,
        "p_align": 0.931
      }, {
        "word": "every ",
        "success": true,
        "start_s": 32.42,
        "end_s": 33.35,
        "p_align": 0.967
      }, {
        "word": "year\n\n",
        "success": true,
        "start_s": 33.35,
        "end_s": 34.26,
        "p_align": 0.998
      }, {
        "word": "[Chorus]\nDeck ",
        "success": true,
        "start_s": 34.27,
        "end_s": 35.23,
        "p_align": 0.653
      }, {
        "word": "the ",
        "success": true,
        "start_s": 35.23,
        "end_s": 35.59,
        "p_align": 0.989
      }, {
        "word": "sky ",
        "success": true,
        "start_s": 35.59,
        "end_s": 36.06,
        "p_align": 0.985
      }, {
        "word": "with ",
        "success": true,
        "start_s": 36.06,
        "end_s": 36.58,
        "p_align": 0.987
      }, {
        "word": "twinkling ",
        "success": true,
        "start_s": 36.58,
        "end_s": 37.46,
        "p_align": 0.779
      }, {
        "word": "stars\n",
        "success": true,
        "start_s": 37.46,
        "end_s": 38.16,
        "p_align": 0.991
      }, {
        "word": "Holiday ",
        "success": true,
        "start_s": 38.2,
        "end_s": 39.45,
        "p_align": 0.988
      }, {
        "word": "joy ",
        "success": true,
        "start_s": 39.45,
        "end_s": 39.93,
        "p_align": 0.997
      }, {
        "word": "feels ",
        "success": true,
        "start_s": 39.93,
        "end_s": 40.45,
        "p_align": 0.019
      }, {
        "word": "ours ",
        "success": true,
        "start_s": 40.45,
        "end_s": 41.13,
        "p_align": 0.592
      }, {
        "word": "and ",
        "success": true,
        "start_s": 41.13,
        "end_s": 41.49,
        "p_align": 0.986
      }, {
        "word": "ours\n",
        "success": true,
        "start_s": 41.49,
        "end_s": 42.25,
        "p_align": 0.624
      }, {
        "word": "Sing ",
        "success": true,
        "start_s": 42.25,
        "end_s": 42.92,
        "p_align": 0.974
      }, {
        "word": "the ",
        "success": true,
        "start_s": 42.92,
        "end_s": 43.4,
        "p_align": 0.954
      }, {
        "word": "songs ",
        "success": true,
        "start_s": 43.4,
        "end_s": 43.88,
        "p_align": 0.964
      }, {
        "word": "of ",
        "success": true,
        "start_s": 43.88,
        "end_s": 44.36,
        "p_align": 0.994
      }, {
        "word": "love ",
        "success": true,
        "start_s": 44.36,
        "end_s": 44.8,
        "p_align": 0.996
      }, {
        "word": "and ",
        "success": true,
        "start_s": 44.8,
        "end_s": 45.28,
        "p_align": 0.99
      }, {
        "word": "light\n",
        "success": true,
        "start_s": 45.28,
        "end_s": 46,
        "p_align": 0.753
      }, {
        "word": "Christmas ",
        "success": true,
        "start_s": 46.01,
        "end_s": 46.95,
        "p_align": 0.995
      }, {
        "word": "glows ",
        "success": true,
        "start_s": 46.95,
        "end_s": 47.83,
        "p_align": 0.018
      }, {
        "word": "so ",
        "success": true,
        "start_s": 47.83,
        "end_s": 48.27,
        "p_align": 0.997
      }, {
        "word": "pure ",
        "success": true,
        "start_s": 48.27,
        "end_s": 48.75,
        "p_align": 0.993
      }, {
        "word": "and ",
        "success": true,
        "start_s": 48.75,
        "end_s": 49.23,
        "p_align": 0.985
      }, {
        "word": "bright\n\n",
        "success": true,
        "start_s": 49.23,
        "end_s": 50.85,
        "p_align": 0.992
      }, {
        "word": "[Verse 3]\nFireside ",
        "success": true,
        "start_s": 55.88,
        "end_s": 58.96,
        "p_align": 0.573
      }, {
        "word": "tales ",
        "success": true,
        "start_s": 58.96,
        "end_s": 59.68,
        "p_align": 0.674
      }, {
        "word": "of ",
        "success": true,
        "start_s": 59.68,
        "end_s": 60.08,
        "p_align": 0.994
      }, {
        "word": "long ",
        "success": true,
        "start_s": 60.08,
        "end_s": 60.68,
        "p_align": 0.998
      }, {
        "word": "ago\n",
        "success": true,
        "start_s": 60.68,
        "end_s": 61.63,
        "p_align": 0.994
      }, {
        "word": "Reindeer ",
        "success": true,
        "start_s": 61.64,
        "end_s": 62.91,
        "p_align": 0.937
      }, {
        "word": "prance ",
        "success": true,
        "start_s": 62.91,
        "end_s": 63.47,
        "p_align": 0.017
      }, {
        "word": "in ",
        "success": true,
        "start_s": 63.47,
        "end_s": 63.95,
        "p_align": 0.062
      }, {
        "word": "icy ",
        "success": true,
        "start_s": 63.95,
        "end_s": 64.83,
        "p_align": 0.951
      },
{
        "word": "glow\n",
        "success": true,
        "start_s": 64.83,
        "end_s": 65.55,
        "p_align": 0.889
      }, {
        "word": "Evergreen ",
        "success": true,
        "start_s": 65.87,
        "end_s": 67.34,
        "p_align": 0.938
      }, {
        "word": "and ",
        "success": true,
        "start_s": 67.34,
        "end_s": 67.66,
        "p_align": 0.986
      }, {
        "word": "tinsel’s gleam\n",
        "success": true,
        "start_s": 69.02,
        "end_s": 69.53,
        "p_align": 0.947
      }, {
        "word": "Christmas ",
        "success": true,
        "start_s": 69.53,
        "end_s": 70.45,
        "p_align": 0.938
      }, {
        "word": "time ",
        "success": true,
        "start_s": 70.45,
        "end_s": 71.29,
        "p_align": 0.731
      }, {
        "word": "a ",
        "success": true,
        "start_s": 71.29,
        "end_s": 71.73,
        "p_align": 0.98
      }, {
        "word": "lovely ",
        "success": true,
        "start_s": 71.73,
        "end_s": 72.13,
        "p_align": 0.99
      }, {
        "word": "dream\n\n",
        "success": true,
        "start_s": 72.13,
        "end_s": 73.03,
        "p_align": 0.994
      }, {
        "word": "[Bridge]\nHearts ",
        "success": true,
        "start_s": 73.25,
        "end_s": 74.16,
        "p_align": 0.995
      }, {
        "word": "are ",
        "success": true,
        "start_s": 74.16,
        "end_s": 74.68,
        "p_align": 0.979
      }, {
        "word": "full ",
        "success": true,
        "start_s": 74.68,
        "end_s": 75.16,
        "p_align": 0.973
      }, {
        "word": "with ",
        "success": true,
        "start_s": 75.16,
        "end_s": 75.6,
        "p_align": 0.985
      }, {
        "word": "friends ",
        "success": true,
        "start_s": 75.6,
        "end_s": 76.12,
        "p_align": 0.996
      }, {
        "word": "and ",
        "success": true,
        "start_s": 76.12,
        "end_s": 76.64,
        "p_align": 0.988
      }, {
        "word": "kin\n",
        "success": true,
        "start_s": 76.64,
        "end_s": 79.64,
        "p_align": 0.927
      }, {
        "word": "Mistletoe ",
        "success": true,
        "start_s": 128.64,
        "end_s": 130.59,
        "p_align": 0.928
      }, {
        "word": "for ",
        "success": true,
        "start_s": 130.81,
        "end_s": 131.53,
        "p_align": 0.98
      }, {
        "word": "love ",
        "success": true,
        "start_s": 131.53,
        "end_s": 132.13,
        "p_align": 0.994
      }, {
        "word": "to ",
        "success": true,
        "start_s": 132.13,
        "end_s": 132.69,
        "p_align": 0.991
      }, {
        "word": "win\n",
        "success": true,
        "start_s": 132.69,
        "end_s": 133.4,
        "p_align": 0.734
      }, {
        "word": "Gifts ",
        "success": true,
        "start_s": 133.57,
        "end_s": 134.8,
        "p_align": 0.572
      }, {
        "word": "of ",
        "success": true,
        "start_s": 134.8,
        "end_s": 135.24,
        "p_align": 0.982
      }, {
        "word": "love ",
        "success": true,
        "start_s": 135.24,
        "end_s": 135.84,
        "p_align": 0.971
      }, {
        "word": "and ",
        "success": true,
        "start_s": 135.84,
        "end_s": 136.48,
        "p_align": 0.918
      }, {
        "word": "hope ",
        "success": true,
        "start_s": 136.48,
        "end_s": 137,
        "p_align": 0.976
      }, {
        "word": "we ",
        "success": true,
        "start_s": 137,
        "end_s": 137.59,
        "p_align": 0.968
      }, {
        "word": "share\n",
        "success": true,
        "start_s": 137.59,
        "end_s": 138.45,
        "p_align": 0.965
      }, {
        "word": "Christmas ",
        "success": true,
        "start_s": 138.55,
        "end_s": 139.81,
        "p_align": 0.954
      }, {
        "word": "spirit ",
        "success": true,
        "start_s": 139.83,
        "end_s": 141.01,
        "p_align": 0.9
      }, {
        "word": "everywhere\n\n",
        "success": true,
        "start_s": 141.08,
        "end_s": 142.71,
        "p_align": 0.281
      }, {
        "word": "[Chorus]\nDeck ",
        "success": true,
        "start_s": 143.4,
        "end_s": 144.69,
        "p_align": 0.298
      }, {
        "word": "the ",
        "success": true,
        "start_s": 144.69,
        "end_s": 145.09,
        "p_align": 0.971
      }, {
        "word": "sky ",
        "success": true,
        "start_s": 145.09,
        "end_s": 145.57,
        "p_align": 0.989
      }, {
        "word": "with ",
        "success": true,
        "start_s": 145.57,
        "end_s": 146.05,
        "p_align": 0.989
      }, {
        "word": "twinkling ",
        "success": true,
        "start_s": 146.05,
        "end_s": 146.93,
        "p_align": 0.776
      }, {
        "word": "stars\n",
        "success": true,
        "start_s": 146.93,
        "end_s": 147.64,
        "p_align": 0.997
      }, {
        "word": "Holiday ",
        "success": true,
        "start_s": 147.65,
        "end_s": 148.84,
        "p_align": 0.986
      }, {
        "word": "joy ",
        "success": true,
        "start_s": 148.84,
        "end_s": 149.32,
        "p_align": 0.996
      }, {
        "word": "feels ",
        "success": true,
        "start_s": 149.32,
        "end_s": 149.84,
        "p_align": 0.826
      }, {
        "word": "ours ",
        "success": true,
        "start_s": 149.84,
        "end_s": 150.52,
        "p_align": 0.819
      },
{
        "word": "y ",
        "success": true,
        "start_s": 150.52,
        "end_s": 150.88,
        "p_align": 0.036
      }, {
        "word": "nuestro\n",
        "success": true,
        "start_s": 150.88,
        "end_s": 151.88,
        "p_align": 0
      }, {
        "word": "Cantar ",
        "success": true,
        "start_s": 151.88,
        "end_s": 152.23,
        "p_align": 0.991
      }, {
        "word": "las ",
        "success": true,
        "start_s": 152.23,
        "end_s": 152.71,
        "p_align": 0.971
      }, {
        "word": "canciones ",
        "success": true,
        "start_s": 152.71,
        "end_s": 153.15,
        "p_align": 0.97
      }, {
        "word": "de ",
        "success": true,
        "start_s": 153.15,
        "end_s": 153.63,
        "p_align": 0.997
      }, {
        "word": "amor ",
        "success": true,
        "start_s": 153.63,
        "end_s": 154.07,
        "p_align": 0.998
      }, {
        "word": "y ",
        "success": true,
        "start_s": 154.07,
        "end_s": 154.55,
        "p_align": 0.997
      }, {
        "word": "luz\n",
        "success": true,
        "start_s": 154.55,
        "end_s": 155.26,
        "p_align": 0.498
      }, {
        "word": "Navidad ",
        "success": true,
        "start_s": 155.26,
        "end_s": 156.18,
        "p_align": 0.988
      }, {
        "word": "brilla ",
        "success": true,
        "start_s": 156.18,
        "end_s": 157.02,
        "p_align": 0.01
      }, {
        "word": "tan ",
        "success": true,
        "start_s": 157.02,
        "end_s": 157.46,
        "p_align": 0.998
      }, {
        "word": "pura ",
        "success": true,
        "start_s": 157.46,
        "end_s": 157.94,
        "p_align": 0.996
      }, {
        "word": "y ",
        "success": true,
        "start_s": 157.94,
        "end_s": 158.38,
        "p_align": 0.986
      },
      {
        "word": "brillante",
        "success": true,
        "start_s": 158.38,
        "end_s": 158.54,
        "p_align": 0.998
      }
    ],
    "waveform_data":
```json
[
      0.02138,
      0.02193,
      0.01806,
      0.16597,
      0.15168,
      0.14243,
      0.15946,
      0.12795,
      0.18192,
      0.15715,
      0.15733,
      0.13223,
      0.10236,
      0.12396,
      0.09187,
      0.04469,
      0.10792,
      0.06101,
      0.10181,
      0.09257,
      0.08039,
      0.10115,
      0.09726,
      0.07491,
      0.10838,
      0.08738,
      0.05148,
      0.08468,
      0.08536,
      0.06077,
      0.04479,
      0.0276,
      0.03204,
      0.02013,
      0.02988,
      0.02696,
      0.02721,
      0.10897,
      0.11125,
      0.08352,
      0.08695,
      0.09652,
      0.11256,
      0.07902,
      0.04354,
      0.07271,
      0.06098,
      0.12638,
      0.08902,
      0.06165,
      0.07618,
      0.06484,
      0.16382,
      0.13887,
      0.1253,
      0.13388,
      0.12615,
      0.14229,
      0.15128,
      0.15587,
      0.14378,
      0.14229,
      0.13766,
      0.12891,
      0.11079,
      0.07877,
      0.14169,
      0.1472,
      0.11916,
      0.13674,
      0.11923,
      0.13518,
      0.13121,
      0.11909,
      0.10013,
      0.08743,
      0.13505,
      0.13245,
      0.17492,
      0.1516,
      0.13873,
      0.15056,
      0.13526,
      0.11973,
      0.11992,
      0.12828,
      0.17955,
      0.14176,
      0.12783,
      0.1555,
      0.13302,
      0.14202,
      0.14726,
      0.14462,
      0.17111,
      0.18055,
      0.14646,
      0.14171,
      0.14681,
      0.14228,
      0.15144,
      0.15389,
      0.1263,
      0.1279,
      0.12469,
      0.14623,
      0.13727,
      0.12244,
      0.12733,
      0.11375,
      0.15587,
      0.11131,
      0.12019,
      0.13293,
      0.13456,
      0.14777,
      0.11358,
      0.15271,
      0.12021,
      0.11216,
      0.17344,
      0.1247,
      0.10261,
      0.10042,
      0.09308,
      0.17905,
      0.17675,
      0.14859,
      0.14566,
      0.12327,
      0.15466,
      0.1168,
      0.13746,
      0.16423,
      0.12185,
      0.1719,
      0.15294,
      0.14453,
      0.1411,
      0.1687,
      0.14121,
      0.12525,
      0.13107,
      0.13383,
      0.16934,
      0.15845,
      0.15338,
      0.14912,
      0.14207,
      0.15669,
      0.14985,
      0.14245,
      0.1103,
      0.10301,
      0.14954,
      0.15229,
      0.1693,
      0.14344,
      0.10428,
      0.17816,
      0.1533,
      0.1471,
      0.13282,
      0.1262,
      0.16628,
      0.14764,
      0.13304,
      0.14822,
      0.15496,
      0.17233,
      0.1201,
      0.08351,
      0.04608,
      0.03659,
      0.21505,
      0.1965,
      0.15394,
      0.16308,
      0.16336,
      0.1718,
      0.14165,
      0.13259,
      0.13197,
      0.16476,
      0.17493,
      0.14789,
      0.14095,
      0.13638,
      0.15559,
      0.17277,
      0.1457,
      0.11338,
      0.1447,
      0.165,
      0.17181,
      0.14981,
      0.14975,
      0.14245,
      0.17455,
      0.15755,
      0.14119,
      0.13639,
      0.13938,
      0.18593,
      0.17839,
      0.1571,
      0.14522,
      0.11204,
      0.16857,
      0.16971,
      0.16993,
      0.1682,
      0.16398,
      0.1838,
      0.16591,
      0.16003,
      0.15509,
      0.133,
      0.18397,
      0.14066,
      0.13304,
      0.12337,
      0.11144,
      0.19632,
      0.17795,
      0.17463,
      0.14889,
      0.18691,
      0.19169,
      0.1523,
      0.13982,
      0.15733,
      0.1675,
      0.1708,
      0.12915,
      0.14241,
      0.10993,
      0.13858,
      0.15916,
      0.11727,
      0.10507,
      0.11202,
      0.09055,
      0.13071,
      0.15836,
      0.17097,
      0.17347,
      0.17533,
      0.15594,
      0.17629,
      0.17451,
      0.18599,
      0.17383,
      0.15985,
      0.15009,
      0.15253,
      0.14552,
      0.17784,
      0.15488,
      0.17318,
      0.1539,
      0.15804,
      0.20072,
      0.16631,
      0.15446,
      0.15721,
      0.17434,
      0.14827,
      0.15718,
      0.16584,
      0.17932,
      0.18599,
      0.16786,
      0.16582,
      0.16052,
      0.15991,
      0.18699,
      0.15267,
      0.15158,
      0.14827,
      0.16479,
      0.17776,
      0.13477,
      0.13523,
      0.18281,
      0.13999,
      0.16943,
      0.1485,
      0.16534,
      0.16554,
      0.14765,
      0.19291,
      0.18703,
      0.18306,
      0.17896,
      0.1363,
      0.14311,
      0.10585,
      0.08122,
      0.08897,
      0.08659,
      0.18905,
      0.16734,
      0.15331,
      0.1414,
      0.14998,
      0.11807,
      0.06647,
      0.04452,
      0.14245,
      0.17684,
      0.1566,
      0.14429,
      0.14291,
      0.13782,
      0.13001,
      0.10448,
      0.08865,
      0.05929,
      0.09944,
      0.15196,
      0.17625,
      0.15286,
      0.15726,
      0.14029,
      0.14204,
      0.10268,
      0.17724,
      0.12196,
      0.09397,
      0.15353,
      0.14013,
      0.1596,
      0.138,
      0.12483,
      0.12917,
      0.10877,
      0.0918,
      0.09902,
      0.08997,
      0.17738,
      0.15788,
      0.13885,
      0.13672,
      0.11215,
      0.1378,
      0.12321,
      0.11722,
      0.10271,
      0.09754,
      0.19296,
      0.11697,
      0.13857,
      0.11691,
      0.1381,
      0.15123,
      0.13411,
      0.1344,
      0.12641,
      0.12332,
      0.08255,
      0.16637,
      0.15984,
      0.18909,
      0.1746,
      0.16538,
      0.20246,
      0.18597,
      0.1633,
      0.18649,
      0.17887,
      0.13832,
      0.15472,
      0.13753,
      0.18149,
      0.13445,
      0.13202,
      0.1313,
      0.09488,
      0.15916,
      0.16066,
      0.14814,
      0.15363,
      0.12768,
      0.16703,
      0.13274,
      0.13768,
      0.1651,
      0.14596,
      0.16804,
      0.15268,
      0.13297,
      0.12703,
      0.12682,
      0.15732,
      0.13211,
      0.14096,
      0.15012,
      0.1597,
      0.16438,
      0.13657,
      0.11582,
      0.17221,
      0.15878,
      0.15468,
      0.15818,
      0.12871,
      0.17567,
      0.18818,
      0.15226,
      0.13384,
      0.14942,
      0.12368,
      0.15595,
      0.13483,
      0.13303,
      0.14397,
      0.14656,
      0.17153,
      0.16251,
      0.13008,
      0.14049,
      0.1419,
      0.17529,
      0.14977,
      0.13763,
      0.16814,
      0.14442,
      0.19431,
      0.13788,
      0.13851,
      0.13477,
      0.11922,
      0.17841,
      0.14847,
      0.14833,
      0.14186,
      0.14319,
      0.19066,
      0.1777,
      0.16641,
      0.1721,
      0.17328,
      0.16013,
      0.17229,
      0.16318,
      0.17146,
      0.19486,
      0.20893,
      0.21136,
      0.17704,
      0.1745,
      0.20083,
      0.1651,
      0.1503,
      0.14384,
      0.18038,
      0.2046,
      0.19477,
      0.17469,
      0.18299,
      0.17138,
      0.19765,
      0.195,
      0.173,
      0.18554,
      0.16669,
      0.20494,
      0.1884,
      0.17792,
      0.17405,
      0.14763,
      0.19321,
      0.16601,
      0.1388,
      0.16073,
      0.1801,
      0.20274,
      0.1842,
      0.17477,
      0.18804,
      0.17548,
      0.18893,
      0.203,
      0.16938,
      0.20182,
      0.19082,
      0.18426,
      0.17852,
      0.17248,
      0.15267,
      0.17086,
      0.14301,
      0.1452,
      0.14305,
      0.19373,
      0.20921,
      0.18247,
      0.16228,
      0.18186,
      0.16932,
      0.20423,
      0.17633,
      0.16076,
      0.18075,
      0.15467,
      0.19785,
      0.16696,
      0.1564,
      0.14855,
      0.13175,
      0.1614,
      0.14633,
      0.11323,
      0.12959,
      0.10203,
      0.0987,
      0.13578,
      0.19891,
      0.19333,
      0.18763,
      0.19431,
      0.18305,
      0.18189,
      0.16428,
      0.17688,
      0.18775,
      0.18099,
      0.18193,
      0.16797,
      0.18287,
      0.16393,
      0.15868,
      0.16615,
      0.16201,
      0.19014,
      0.19001,
      0.18501,
      0.17374,
      0.16571,
      0.18199,
      0.14724,
      0.16591,
      0.17586,
      0.17535,
      0.19552,
      0.17702,
      0.17228,
      0.17465,
      0.17223,
      0.18529,
      0.16955,
      0.18701,
      0.17093,
      0.17808,
      0.19186,
      0.19837,
      0.18237,
      0.18759,
      0.1562,
      0.14025,
      0.16039,
      0.15504,
      0.17413,
      0.13696,
      0.1809,
      0.16813,
      0.16541,
      0.15887,
      0.1737,
      0.17135,
      0.158
aligned_words

It can be seen that the `aligned_words` field of `data` is an array of objects, each representing a word or phrase with time information. The meanings of the other fields in `aligned_words` are as follows:
`word`: The actual word or phrase in the lyrics
`success`: A boolean value indicating whether the alignment of this word was successful
`start_s`: The start time of the word
`end_s`: The end time of the word
`p_align`: The probability or confidence score of the alignment (range 0-1)