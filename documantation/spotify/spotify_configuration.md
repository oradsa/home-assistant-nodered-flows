# Spotify  configuration
The spotify property in the nodered-configuration.json file holds the Soptify configuration.

## Configuration
   
&nbsp;**spotify** &nbsp; *object* <br>
&nbsp;&nbsp;&nbsp; Map of `spotify configuration` objects, see below.

&nbsp;&nbsp;&nbsp;&nbsp; **default** *string* or *object* `optional` <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Either *string* specifing the name of the default configuration to use, or the `spotify configuration` object itself (see below).

&nbsp;&nbsp;&nbsp;&nbsp; **<custom_name>** *object* <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Define a spotify instance configuration see `spotify configuration` object below.

### Spotify configuration object options

&nbsp;**authorization** &nbsp; *object* <br>
&nbsp;&nbsp;&nbsp; Set authorization options. See details below on how to get authorization details.

&nbsp;&nbsp;&nbsp;&nbsp; **type** *string* <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `api_token` or `web_player_token`. See authorization section below.

&nbsp;&nbsp;&nbsp;&nbsp; **clientId** *string* <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; The client id. Relevant only for `api_token` authorization type.

&nbsp;&nbsp;&nbsp;&nbsp; **clientSecret** *string* <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; The client secret. Relevant only for `api_token` authorization type.

&nbsp;&nbsp;&nbsp;&nbsp; **refreshToken** *string* <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; The refresh token. Relevant only for `api_token` authorization type.

&nbsp;&nbsp;&nbsp;&nbsp; **sp_dc** *string* <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; The value of `sp_dc` cookie. Relevant only for `web_player_token` authorization type.

&nbsp;&nbsp;&nbsp;&nbsp; **sp_t** *string* <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; The value of `sp_t` cookie. Relevant only for `web_player_token` authorization type.

&nbsp;**defaultDevice** &nbsp; *string* `optional` <br>
&nbsp;&nbsp;&nbsp; Name of a device to use in case no device specified and none is currently playing.

&nbsp;**playlistNicknames** &nbsp; *object* `optional` <br>
&nbsp;&nbsp;&nbsp; Custom playlist nicknames.

&nbsp;&nbsp;&nbsp;&nbsp; **<playlist_name_or_uri>** *array of strings* <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; The playlist exact name or Spotify URI of the playlist. The value is an array of strings which are the nicknames of the playlist.

&nbsp;**ignoredCharsWhenComparingNames** &nbsp; *array of strings* `optional` <br>
&nbsp;&nbsp;&nbsp; Define characters to ignore when a playlist is being searched by its name. Default: `['(',')','-']`.

### Authorization
There are 2 authorization types. Notice that only `web_player_token` authorization supports Sonos playback.

#### api_token authorization
You'll need a client id, client secret, and a refresh token.

To generate those, refer to https://developer.spotify.com/dashboard/applications and create a new application, and then follow the [Spotify authorization guide](https://developer.spotify.com/documentation/general/guides/authorization-guide/#authorization-code-flow).

#### web_player_token authorization
You'll need the value of the `sp_dc` and `sp_t` cookies from a Spotify Web Player session.

It's best to open the browser in incognito mode, then open `https://open.spotify.com` and login. 
Afterwards, open the developer tools of your browser and get the values of the relevant cookies.
You can assist [this guide](https://developers.google.com/web/tools/chrome-devtools/storage/cookies) if needed.

## Example of Complete configuration section

```json
"spotify": {
  "default": "my_spotify",
  "my_spotify": {
    "entityId": "media_player.spotify",
    "authorization": {
      "type": "api_token|web_player_token",
      "clientId": "in case you use 'api_token' authorization type",
      "clientSecret": "in case you use 'api_token' authorization type",
      "refreshToken": "in case you use 'api_token' authorization type",
      "sp_dc": "in case you use 'web_player_token' authorization type, check readme",
      "sp_t": "in case you use 'web_player_token' authorization type, check readme"
    },
    "playlistNicknames": {
      "spotify:playlist:xxx": [
        "Daily Mix 1"
      ]
    }
  }
}
```

