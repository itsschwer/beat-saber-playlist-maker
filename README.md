# beat saber playlist maker

[![Live version](https://img.shields.io/badge/live_ver.-0D1117?logo=github)](https://itsschwer.github.io/beat-saber-playlist-maker/bplist.html)

A single-file .html to extract BeatSaver map links from text and turn it into a playlist.

## to-do
- *ideally:*
    - populate (using api?) song `hash` (for mod/manager compatibility) and `songName` (for user readability if editing via text)
        - https://api.beatsaver.com/docs/index.html#/OrderedMap%20%7B%20%22name%22%3A%20%22Maps%22%20%7D/get_maps_ids__ids_
        - https://github.com/FranciscoRibeiro03/beatsaver-api

## notes
- BSManager can find and download maps from keys but won't properly populate the playlist view (will show correct number of maps in summary stats but won't read length or NPS, and (maybe??) won't display songs in list)
- these maps also won't show in the playlist in-game (but are correctly downloaded and visible in custom levels tab)
    - may stem from the playlist library(?) not supporting loading maps by key alone
        - ∴ use PlaylistManager to "download" the missing maps ([which populates hash field using key](https://github.com/rithik-b/PlaylistManager/blob/7df198c81877c87376995d4aea493fb1ab014866/PlaylistManager/Downloaders/PlaylistSequentialDownloader.cs#L278-L306))

## samples

#### bs manager
```json
{
  "image": "",
  "playlistAuthor": "TESTING",
  "playlistTitle": "test",
  "playlistDescription": "",
  "songs": [
    {
      "hash": "4a792f734838a1b2d8346e8ecd7afdd2046a925b",
      "key": "65d0",
      "songName": "Cyberpunk 2077 Trailer Music"
    }
  ]
}
```

#### existing + new key
```json
{
  "playlistTitle": "TESTING",
  "playlistAuthor": "test",
  "playlistDescription": "",
  "songs": [
    {
      "key": "13E9",
      "songName": "BUBBLE TEA",
      "hash": "F83EDEC86D3FAF683711ECB0A9DF6BD65D2D0CE0",
      "levelid": "custom_level_F83EDEC86D3FAF683711ECB0A9DF6BD65D2D0CE0"
    },
    {"key": "155"}
  ],
  "image": ""
}
```

#### playlist manager (in-game mod)?
```json
{
  "playlistTitle": "TESTING",
  "playlistAuthor": "test",
  "playlistDescription": "",
  "songs": [
    {
      "key": "13E9",
      "songName": "BUBBLE TEA",
      "hash": "F83EDEC86D3FAF683711ECB0A9DF6BD65D2D0CE0",
      "levelid": "custom_level_F83EDEC86D3FAF683711ECB0A9DF6BD65D2D0CE0"
    },
    {
      "key": "155",
      "hash": "FBD8B9338BFFB98555A10C69887234FAC959D83D",
      "levelid": "custom_level_FBD8B9338BFFB98555A10C69887234FAC959D83D"
    }
  ],
  "image": ""
}
```
