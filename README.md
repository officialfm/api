# Official.fm API v2

This is the reference guide of all the resources available on Official.fm API v2.

## Current version

You must specify the API version using the header `X-API-Version` or the parameter `api_version`.

For example, accessing the URL <http://api.official.fm/greeting?api_version=2> will return the following object:

```javascript
{
  'greeting': 'Hi there! You are successfully authenticated for keyless access.'
}
```

## General information

  * [Authentication](https://github.com/officialfm/api/blob/master/sections/authentication.md)
  * [Pagination](https://github.com/officialfm/api/blob/master/sections/pagination.md)

The only output format supported by the API is JSON.

## Endpoints

### Projects

  * Endpoints
    * Get a single project: <http://api.official.fm/projects/:ID?api_version=2>
    * Get tracks of a project: <http://api.official.fm/projects/:ID/tracks?api_version=2>
    * Get playlists of a project: <http://api.official.fm/projects/:ID/playlists?api_version=2>
    * Search for projects: <http://api.official.fm/projects/search?q=mac&api_version=2>

  * Optional fields
    * Cover: <http://api.official.fm/projects/SeMD?fields=cover&api_version=2>

Examples:
<http://api.official.fm/projects/SeMD?fields=cover&api_version=2>

```javascript
{
  "project": {
    "name": "Mac Miller & Pharrell",
    "url": "http://api.official.fm/projects/SeMD?api_version=2",
    "page": null,
    "tracks_count": 1,
    "cover": {
      "urls": {
        "large": "http://cdn.official.fm/medias/pictures/3t/3tJI_large.jpg",
        "medium": "http://cdn.official.fm/medias/pictures/3t/3tJI_medium.jpg",
        "small": "http://cdn.official.fm/medias/pictures/3t/3tJI_small.jpg",
        "tiny": "http://cdn.official.fm/medias/pictures/3t/3tJI_tiny.jpg"
      },
      "id": "3tJI"
    },
     "playlists_count": 0
  }
}
```

### Playlists

  * Endpoints
    * Get a single playlist: <http://api.official.fm/playlists/:ID?api_version=2>
    * Get a single playlist with embed fields: <http://api.official.fm/playlists/:ID?fields=embed&api_version=2>
    * Get tracks of a playlist: <http://api.official.fm/playlists/:ID/tracks?api_version=2>
    * Search for playlists: <http://api.official.fm/playlists/search?q=mac&api_version=2>

  * Optional fields
    * Embed: <http://api.official.fm/playlists/1rp7?fields=embed&api_version=2>

Example:
<http://api.official.fm/playlists/1rp7?fields=embed&api_version=2>

```javascript
{
  "playlist": {
    "name": "Macadelic",
    "url": "http://api.official.fm/playlists/1rp7?api_version=2",
    "page": "http://official.fm/playlists/1rp7",
    "rough_view_count": null,
    "rough_play_count": null,
    "rough_download_count": null,
    "tracks_count": 15,
    "embed": {
      "code": "<iframe width='400' height='40' src='http://official.fm/player?skin_bg=000000&skin_fg=FFFFFF&width=400&height=40&feed=http%3A%2F%2Fofficial.fm%2F%2Ffeed%2Fplaylists%2F1rp7' frameborder='0'></iframe>"
    },
    "project": {
      "name": "Mac Miller",
      "url": "http://api.official.fm/projects/f8w6?api_version=2"
    }
  }
}
```

### Tracks

  * Endpoints
    * Get a single track: <http://api.official.fm/tracks/:ID?api_version=2>
    * Get a single track with streaming and/or cover and/or embed fields: <http://api.official.fm/tracks/:ID?fields=streaming,cover,embed&api_version=2>
    * Search for tracks: <http://api.official.fm/tracks/search?q=mac&api_version=2>

  * Optional fields
    * Streaming: <http://api.official.fm/tracks/D4lw?fields=streaming&api_version=2>
    * Cover: <http://api.official.fm/tracks/D4lw?fields=cover&api_version=2>
    * Embed: <http://api.official.fm/tracks/D4lw?fields=embed&api_version=2>

Example:
<http://api.official.fm/tracks/D4lw?fields=streaming,cover,embed&api_version=2>

```javascript
{
  "track": {
    "title": "Love Me As I Have Loved You (prod. Ritz Reynolds)",
    "duration": 75,
    "artist": "Mac Miller",
    "url": "http://api.official.fm/tracks/D4lw?api_version=2",
    "page": "http://official.fm/tracks/D4lw",
    "rough_view_count": null,
    "rough_play_count": null,
    "rough_download_count": null,
    "streaming": {
      "http": "http://api.official.fm/tracks/D4lw/stream?api_version=2",
      "rtmp": "rtmpe://fairtilize-174.fcod.llnwd.net/a2251/r2/mp3:/audio2/s/D4/D4lw_3594640?h=949ae69d743987d2cf46801c8ef9485a"
    },
    "cover": {
      "urls": {
        "large": "http://cdn.official.fm/medias/pictures/tu/tuKi_large.jpg",
        "medium": "http://cdn.official.fm/medias/pictures/tu/tuKi_medium.jpg",
        "small": "http://cdn.official.fm/medias/pictures/tu/tuKi_small.jpg",
        "tiny": "http://cdn.official.fm/medias/pictures/tu/tuKi_tiny.jpg"
      },
      "id": "tuKi"
    },
    "embed": {
      "code": "<iframe width='400' height='40' src='http://official.fm/player?skin_bg=000000&skin_fg=FFFFFF&width=400&height=40&feed=http%3A%2F%2Fofficial.fm%2F%2Ffeed%2Ftracks%2FD4lw' frameborder='0'></iframe>"
    },
    "project": {
      "name": "Mac Miller",
      "url": "http://api.official.fm/projects/f8w6?api_version=2"
    }
  }
}
```

## Bindings

  * [Ruby](https://github.com/officialfm/officialfm-v2-ruby)
  * [PHP](https://github.com/officialfm/officialfm-v2-php)

## Issues or Questions?

Questions about the API can be asked by [opening an issue](https://github.com/officialfm/api/issues/new) for this project, or contacting us privately [api@official.fm](mailto:api@official.fm).
