# Spotify  configuration
The spotify property in the nodered-configuration.json file holds the Soptify configuration.

## Configuration
   
&nbsp; **spotify** &nbsp; *object* <br>
&nbsp; Map of `spotify configuration` objects, see below.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **default** *string* or *object* &nbsp; `optional` <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Either *string* specifing the name of the default configuration to use, or the `spotify configuration` object itself (see below).

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **<custom_name>** *object* <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Define a spotify instance configuration see `spotify configuration` object below.

### Spotify configuration object options

&nbsp; **authorization** &nbsp; *object* <br>
&nbsp; Set authorization options. See details below on how to get authorization details.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **type** &nbsp; *string* <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `api_token` or `web_player_token`. See authorization section below.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **client_id** &nbsp; *string* <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; The client id. Relevant only for `api_token` authorization type.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **client_secret** &nbsp; *string* <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; The client secret. Relevant only for `api_token` authorization type.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **refresh_token** &nbsp; *string* <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; The refresh token. Relevant only for `api_token` authorization type.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **sp_dc** &nbsp; *string* <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; The value of `sp_dc` cookie. Relevant only for `web_player_token` authorization type.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **sp_key** &nbsp; *string* <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; The value of `sp_key` cookie. Relevant only for `web_player_token` authorization type.

&nbsp; **default_device** &nbsp; *string* &nbsp; `optional` <br>
&nbsp; Name of a device to use in case no device specified and none is currently playing.

&nbsp; **device_aliases** &nbsp; *object* &nbsp; `optional` <br>
&nbsp; Custom device aliases.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **<device_id>** &nbsp; *array of strings* <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; The Spotify device id. The value is an array of strings which are the aliases of the device.

&nbsp; **playlist_aliases** &nbsp; *object* &nbsp; `optional` <br>
&nbsp; Custom playlist aliases.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **<playlist_name_or_uri>** &nbsp; *array of strings* <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; The playlist exact name or Spotify URI of the playlist. The value is an array of strings which are the aliases of the playlist.

&nbsp; **ignored_chars_when_comparing_names** &nbsp; *array of strings* &nbsp; `optional` <br>
&nbsp; Define characters to ignore when a playlist is being searched by its name. Default: `['(',')','-']`.

## Authorization
There are 2 authorization types. Notice that only `web_player_token` authorization supports Sonos playback.

### api_token authorization
You'll need a client id, client secret, and a refresh token.

To generate those, refer to https://developer.spotify.com/dashboard/applications and create a new application, and then follow the [Spotify authorization guide](https://developer.spotify.com/documentation/general/guides/authorization-guide/#authorization-code-flow).

### web_player_token authorization
You'll need the value of the `sp_dc` and `sp_key` cookies from a Spotify Web Player session.

It's best to open the browser in incognito mode, then open `https://open.spotify.com` and login. 
Afterwards, open the developer tools of your browser and get the values of the relevant cookies.
You can assist [this guide](https://developers.google.com/web/tools/chrome-devtools/storage/cookies) if needed.

## Example of Complete configuration section

```json
"spotify": {
  "default": "my_spotify",
  "my_spotify": {
    "authorization": {
      "type": "web_player_token",
      "sp_dc": "<sp_dc_cookie_value>",
      "sp_key": "<sp_key_cookie_value>"
    },
    "default_device": "MySpotifySpeaker",
    "playlist_aliases": {
      "spotify:playlist:xxx": [
        "Daily Mix 1"
      ]
    }
  },
  "other_spotify": {
    "authorization": {
      "type": "api_token",
      "client_id": "<client_id>",
      "client_secret": "<client_secret>",
      "refresh_token": "<refresh_token>"
    }
  }
}
```

