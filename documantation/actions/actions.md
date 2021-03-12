# Actions

## List of supported actions
* [State preservation](/statePreservation.md) - saving or restoring state of devices, filtering by domains and/or entities.
* [Turn off](/turnOff.md) - turn off any device which supports it, filtering by domains and/or entities.
* [Media](/media.md) - control `media_player` entities (play/resume, pause).
* [Climate](/climate.md) - control `climate` entities (turn on/off, set temperature).
* [Cover](/cover.md) - control `cover` entities (open, close, set position).
* [Spotify](/spotify.md) - Spotify playlists playback, to any Spotify device/speaker.
* [Scene](/scene.md) - apply scenes.
* [Service](/service.md) - running any HA service.

## Configurations that can be done on any type of action
The following configuration can be done on any type of action:

&nbsp; **active** &nbsp; *boolean* &nbsp; `optional` <br>
&nbsp; Whether the action is active or not.

&nbsp; **offsetSeconds** &nbsp; *number* &nbsp; `optional` <br>
&nbsp; The number of seconds to postpone the action. Only positive number is allowed.

&nbsp; **restrictions** &nbsp; *object* &nbsp; `optional` <br>
&nbsp; Define set of restrictions that only when met the actions will run.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **mustBeAtHome** &nbsp; *boolean*, *string* or *array of strings* &nbsp; `optional` <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Use `true` to not restricting the person that needs to be at home. <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Use `"<person>"` (string) to specify which person needs to be at home.<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Use `["<person_1>","<person_2>"]` (array of strings) to specify that one of persons needs to be at home.

