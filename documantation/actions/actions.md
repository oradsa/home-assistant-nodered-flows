# Actions

## List of supported actions
* [State preservation](/documantation/actions/statePreservation.md) - saving or restoring state of devices, filtering by domains and/or entities.
* [Turn off](/documantation/actions/turnOff.md) - turn off any device which supports it, filtering by domains and/or entities.
* [Media](/documantation/actions/media.md) - control `media_player` entities (play/resume, pause).
* [Climate](/documantation/actions/climate.md) - control `climate` entities (turn on/off, set temperature).
* [Cover](/documantation/actions/cover.md) - control `cover` entities (open, close, set position).
* [Spotify](/documantation/actions/spotify.md) - Spotify playlists playback, to any Spotify device/speaker.
* [Scene](/documantation/actions/scene.md) - apply scenes.
* [Service](/documantation/actions/service.md) - running any HA service.

## The `actions` object
The `actions` object can be:
1. An *object* with the set of options mentioned below.
2. A *string* specifing the path under the root `actions` object in the `nodered-configuration.json` file, where the actual `actions` object is at.
   See [Multiple usages of the same actions object](#multiple-usages-of-the-same-actions-object) section below.

## Actions object options
The following configuration can be done on `actions` object:

&nbsp; **active** &nbsp; *boolean* &nbsp; `optional` <br>
&nbsp; Whether the action is active or not. Defaults to true.

&nbsp; **offsetSeconds** &nbsp; *number* &nbsp; `optional` <br>
&nbsp; The number of seconds to postpone the action. Only positive number is allowed.

&nbsp; **restrictions** &nbsp; *object* &nbsp; `optional` <br>
&nbsp; Define set of restrictions that only when met the actions will run.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **mustBeAtHome** &nbsp; *boolean*, *string* or *array of strings* &nbsp; `optional` <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Use `true` to not restricting the person that needs to be at home. <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Use `"<person>"` (string) to specify which person needs to be at home.<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Use `["<person_1>","<person_2>"]` (array of strings) to specify that one of persons needs to be at home.


## Nested action object options
Each specific action nested under the `actions` object supports the following options:

&nbsp; **active** &nbsp; *boolean* &nbsp; `optional` <br>
&nbsp; Whether the action is active or not. Defaults to true.

&nbsp; **offsetSeconds** &nbsp; *number* &nbsp; `optional` <br>
&nbsp; The number of seconds to postpone the action. Only positive number is allowed.

## Multiple usages of the same actions object
If you want to execute the same set of actions from multiple triggers, you can replace the actual `actions` object with a string specifing the path of the actual `actions` object. The path of this object should always be under `actions` root object of the `nodered-configuration.json` file.

For example, if the `nodered-configuration.json` file contains the following:
```
{
  ...
  "actions": {
    "my_named_actions": {
      ...
      <spcific actions to run>
      ...
    },
    "parent_prop": {
      "my_nested_named_actions": {
        ...
        <spcific actions to run>
        ...
      }
    }
  }
  ...
}
```
Then the you can put `"my_named_actions"` or `"parent_prop.my_nested_named_actions"` intead of putting the complete object multiple times.
All other options that are supported under the `actions` object could be set on this object as well (e.g. `offsetSeconds`).

