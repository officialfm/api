# Player API

There are 2 type of players:
  - Headless Player:  Audio only, you handle the design & UI. [demo page](http://jsfiddle.net/85LX8/)
  - Official.fm Player: Standard Ofm players [demo page](http://jsfiddle.net/p6ecF/)

### Usage: 

Simply include our latest Player API JS library in your HTML document:

    <script src="http://cdn.official.fm/api/player1.0.js" type="text/javascript"></script> 


### Versions: 
1.0, Sept 2012: First version of both headless player & player.


# 1. Headless Player

[demo page](http://jsfiddle.net/85LX8/)

var player = new OfficialFM.HeadlessPlayer(options)

```javascript
Example:

new OfficialFM.HeadlessPlayer({
  type: 'tracks',
  ids: ['abcd','efgh','ijkl'],
  listener: function(player, event, data){
    console.log('player event:', player, event, data)
  }
});
```

## Options

```javascript
options (object): player options

type (string): ['tracks'], 'track' or 'playlist'
   Type of resource you want the player to play (a track, a list of tracks or a playlist)

id (string):
  ID of a the resource (track ID when type is 'track' or a playlist ID when type is 'playlist')

ids (array or comma-separated string):
  List of track IDs when type is 'tracks'. Array (['abcd', 'efgh']) or a comma-separated string of IDs ('abcd, efgh')

autoplay (boolean):
  Autoplay on load?

listener (function): 
  Event listener - listens for events like playing, paused, track has changed... more on this below.
```

## Listener:

Listener arguments:
```javascript
listener: function(player, event, data){
  console.log(player, 'this is the player instance, the same object as returned by "new OfficialFM.HeadlessPlayer(..)"');
  console.log(event, 'the player event as string');
  console.log(data, 'additional event data, not used at the moment.');
}
```

Events list:
```javascript
'PLAY': Player starts playing
'PAUSE': Player is paused.
'TRACK': Player changed track. You may want to get new track info here (artist/title..)
'END': Tracklist or playlist ended. You may want to start something else when this event is fired; start playing another player, restart player, play a video of a kitten, etc...
'TIME': Whenever player time info (duration, current position...) has changed. Called ~twice per seccond when player is loading or playing.
'SHOW_SPINNER': Use to display some sort of loading icon or message when the player busy.
'HIDE_SPINNER': Use to hide said loading icon or message when the player is no longer inconvenienced.
```

Callbacks:
```javascript
playTrack(ids)
  Load and play a single track (playTrack('abcd')) or list of tracks(playTrack('abcd, efgh') or playTrack(['abcd', 'efgh']))

playPlaylist(id)
  Load and play a playlist (playPlaylist('abcd'))

play()
  Play current track

pause()
  Pause current track

next()
  Move to next track

previous()
  Move to previous track

seek(sec):
  Move playing head at sec seconds

seekPerc(perc):
  Move playing head at perc % of the track duration

playing(): boolean
  Player is playing or paused

track(): object
  Current track info hash, containing:
  {
    id (string): ofm track id,
    artist (string): artist/band name,
    title (string): track title,
    permalink(string) : track official.fm promo page url,
    artwork(string): track artwork url
  }

position(): int:
  Player position in seconds

positionPretty(): string:
  Player position formatted "MM:SS"

positionPerc(): int:
  Player position in percentage

duration(): int: 
  Track duration in seconds

durationPretty: string:
  Track duration formatted "MM:SS"
```

# 2. Official.fm Player

[demo page](http://jsfiddle.net/p6ecF/)

var player = new OfficialFM.Player(containerId, [options])

```javascript
example:
  new OfficialFM.Player('container-id', {
    type: 'tracks',
    ids: ['W2Kb','tuzg','E6fW'],
    autoplay: true,
    artwork: true,
    tracklist: true,
    artwork_left: true,
    width: 500,
    skin_bg: 'FFFFFF',
    skin_fg: '000066'
  });
```

## Options

```javascript
containerId (string): 
  Targetted DOM element ID where the player will be created.

options (object): player options

  type (string): ['tracks'], 'track', 'playlist']: 
    Type of resource you want the player to play (a track, a list of tracks or a playlist).

  id (string): 
    ID of a the resource (track ID when type is 'track' or a playlist ID when type is 'playlist')

  ids (array or comma-separated string):
    List of track IDs when type is 'tracks'. Array (['abcd', 'efgh']) or a comma-separated string of IDs ('abcd, efgh')

  autoplay (boolean): 
    Autoplay on load

  listener: (function): 
    Event listener (listen for events such as: playing, paused, track has changed...)

  aspect (string): 'tiny', ['modular']: 
    Tiny is the minimal "play button only" player, modular is the highly customizable player (see tracklist, artwork, control, artworkLeft options below).

  width (int or string): 
    Player width in pixel integer (ex. 200) or percentage string ("100%").

  artwork (boolean):
    When type is 'modular', the player will contain the artwork module.

  tracklist (boolean): 
    When type is 'modular', the player will contain the tracklist module.

  control (boolean):
    When type is 'modular', the player will contain the controller module.  The controller module includes a play button, start and end times and the timeline.

  artworkLeft (boolean):
    When artwork & tracklist above are enabled, this will position the artwork on the left of the tracklist.

  skin_bg: '000000'
    This will be the primary background color of the player.  

  skin_fg: 'FFFFFF'
    This will be the primary foreground color of the player (text, icons, etc).
```

## Tips

_**css**: Because the player will sit in your DOM, we'll be sharing your CSS. Our player styles are always scoped and should not intefere with your styles (but let us know if it does!), but you could still break the player styles by being too generic with your CSS selectors (ex: div {background-color: pink !important}). So beware..._

_**player height**: You can specify a height (int) in the OfficialFM.Player options but you should only do so to fix layout problems. Height is automaticly calculated base on other options(width, modules used). We suggest you start without and try tweaking it if the player doesn't look as expected._


## Listener
see HeadlessPlayer "Listener" above.

## Events
see HeadlessPlayer "Events" above.

## Callbacks
see HeadlessPlayer "Callbacks" above.


## Issues or Questions?

Questions about the API can be asked by [opening an issue](https://github.com/officialfm/api/issues/new) for this project, or contacting us privately [api@official.fm](mailto:api@official.fm).
