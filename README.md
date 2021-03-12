# Home Assistant NodeRED flows
Extending [Home Assistant](http://home-assistant.io) by [Node-RED](http://nodered.org) flows.

## Features

* Triggers that are supported:
  * Zone presence (e.g. person is at home).
  * Alarm time from phone (requires phone app).
  * State changes (e.g. pause music when the phone is ringing).
  * Schedule (e.g. specific time at day, or sunrise/sunset).
  * Custom triggers from HA scripts (e.g. to connect a script to Google Assistant and run its actions by Node-RED).
* Actions that could be run:
  * Save currrent state or restore it (e.g. when leaving/comming back home).
  * Turning devices off, by entire domains or entities filtering.
  * Media player pausing and resuming.
  * Climate setting to specific temperature, turning on/off, and cycling on-off for defined times.
  * Cover opening, closing, setting to specific position, or changing position by steps (e.g. slow opening at morning).
  * Spotify playback for playlists, and to any device (supports Sonos devices).
  * Appling scenes.
  * Running any other HA service.
* Ability to use HA UI to change the configuration (e.g. enable/disable scenarios).
* Allowing usage of targeted actions multiple times.

## How to install
First, validate that all the dependencies are met, then continue to the Install or update section.

### Dependencies
1. You must have Home Assistant installed.
2. You should have [Home Assistant Node-RED addon](https://github.com/hassio-addons/addon-node-red) installed. If it doesn't, you need to set the HA server node manually to connect to your HA instance.
3. You must have Node-RED installed.
4. Within Node-RED, make sure the following modules are installed (though the top-right menu > Manage palette):
   * node-red-contrib-home-assistant-websocket
   * node-red-contrib-calendar-trigger
   * node-red-contrib-schedex

### Install or update
**Notice**: when updating, save the current latitude & longitude of the Schedex node before you import the updated flows.
1. Download the flows `.json` files from the [flows](/flows) folder.
2. Import the flows `.json` files into Node_RED (through the top-right menue > Import).
3. If you're not using the Home Assistant Node-RED addon, set the Home Assistant server node manually (through the top-right menue > Configuration nodes > Home Assistant).
4. Set the latitude & longitude of the Schedex node. You can find them by clicking on a spot on a map inside [Google Maps](http://maps.google.com).
5. Download the  from [config](/config) folder, and place it under your `/config` folder inside Home Assistant.
   > If you're running Node-RED outside of HA, create a `/config` folder under the root folder where Node-RED is running, and place the file there.
7. Deploy the flows to Node-RED.

## Configuration
All the configuration is done on the `nodered-configuration.json` file.
You can find a complete example for the configuration file [here](/config/nodered-configuration.json).

The `nodered-configuration.json` file contains the following main sections:
* **events** - this is the triggers section.
* **actions** - here you can define actions that you want to reffer to from multiple triggers, if needed.
* **spotify** - contains the configuration and authorization for Spotify playback.
* **inputEntitiesToConfigMap** - configuration for input entities that can control the Node-RED configuration file.

### Events (triggers)
The `events` property in the `nodered-configuration.json` file allows you to configure the following triggers:
* [Presence](/documantation/events/presence.md) - triggered when a persone detected at a zone.
* [Alarm](/documantation/events/alarm.md) - triggered when the phone alarm goes off.
* [states](/documantation/events/states.md) - triggered when an entity state is changed, to a specific value(s).
* [schedule](/documantation/events/schedule.md) - triggered at a specific schedule (e.g. time of day).
* [Custom events](/documantation/events/custom_events.md) - triggered manually (e.g. by HA script).

### Actions
The `actions` property in the `nodered-configuration.json` file allows you to [configure actions that you use multiple times](/documantation/actions/actions.md).

The actions that you can define:
* [statePreservation](/documantation/actions/statePreservation.md) - saving or restoring state of devices, filtering by domains and/or entities.
* [turnOff](/documantation/actions/turnOff.md) - turn off any device which supports it, filtering by domains and/or entities.
* [media](/documantation/actions/media.md) - control `media_player` entities (play/resume, pause).
* [climate](/documantation/actions/climate.md) - control `climate` entities (turn on/off, set temperature).
* [cover](/documantation/actions/cover.md) - control `cover` entities (open, close, set position).
* [spotify](/documantation/actions/spotify.md) - Spotify playlists playback, to any Spotify device/speaker.
* [scene](/documantation/actions/scene.md) - apply scenes.
* [service](/documantation/actions/service.md) - running any HA service.

### Spotify
The `spotify` property in the `nodered-configuration.json` file holds the Soptify configuration.

Reffer to [Spotify configuration](/documantation/spotify/spotify_configuration.md) documanation for more info.

### Input entities control
The `inputEntitiesToConfigMap` property in the `nodered-configuration.json` file allows to configure [input entities](https://www.home-assistant.io/integrations/#search/input_) that can control the Node-RED configuration file. This is helpful when you want to be able to change certain configuraitons from the UI on the fly instead of opening the configuration file to change them.

Reffer to [Input entities control](/documantation/inputEntitiesToConfigMap/inputEntitiesToConfigMap.md) documanation for more info.
