# Input entities control

The `input_entities_to_config_map` property in the `nodered-configuration.json` file allows to configure [input entities](https://www.home-assistant.io/integrations/#search/input_) that can control the Node-RED configuration file. This is helpful when you want to be able to change certain configuraitons from the UI on the fly instead of opening the configuration file to change them.

## Configuration
   
&nbsp; **input_entities_to_config_map** &nbsp; *object* <br>
&nbsp; Dictionary/hashmap from the input entity id to the path of the property which it control.

**Notice**: The name of the input entity must begin with `nr_config_`, e.g. for input_boolean, use a name like `input_boolean.nr_config_xxx`. 

## Supported input entity types
* input_boolean - for boolean (true/false) properties
* input_number - for numeric properties
* input_text - for textual properties
* input_select - for textual properties, by its value

## Example of Complete configuration section

```json
"input_entities_to_config_map": {
  "input_boolean.nr_config_alarm_active": "events.alarm.my_phone_next_alarm.active",
  "input_number.nr_config_alarm_cover_position": "events.alarm.my_phone_next_alarm.actions.cover.my_cover.position"
}
```

