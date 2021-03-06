# State Preservation action

Preserves states for selected domains and/or entities, or restores a previously preserved states.

## Configuration
   
&nbsp; **state_preservation** &nbsp; *object* <br>
&nbsp; Define to use the State Preservation action.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **action** *string* <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `save` or `restore`.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **include** *object* &nbsp; `optional` <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Define domains or entities to save states for. Relevat only when `action`=`save`. <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Either this or `exclude` option must be set, with either `domains` or `entities` under it. <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; If the include object is not defined, all entities except excluded domains and entities will be saved.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **domains** *list of strings* &nbsp; `optional` <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Define domains to save states for.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **entities** *list of strings* &nbsp; `optional` <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Define entities to save states for.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **exclude** *object* &nbsp; `optional` <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Define domains or entities to never save states for. Relevat only when `action`=`save`. <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Either this or `include` option must be set, with either `domains` or `entities` under it.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **domains** *list of strings* &nbsp; `optional` <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Define domains to never save states for.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **entities** *list of strings* &nbsp; `optional` <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Define entities to never save states for.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **hours_to_expire** *inteter* &nbsp; `optional` <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Number of hours the saved states will be valid. Relevat only when `action`=`save`. Cannot be set together with `minutesToExpire`.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **minutes_to_expire** *inteter* &nbsp; `optional` <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Number of minutes the saved states will be valid. Relevat only when `action`=`save`. Cannot be set together with `hoursToExpire`.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **ignore_states** *list of strings* &nbsp; `optional` <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; List of states to ignore while saving states. Relevat only when `action`=`save`. Default: `["off","idle"]`.


## Example of complete configuration section
Saving states for all `climate` and `switch` entities, except of `switch.my_switch`:
```json
"state_preservation": {
  "action": "save",
  "include": {
    "domains": [
      "climate",
      "switch"
    ]
  },
  "exclude": {
    "entities": [
      "switch.my_switch"
    ]
  }
}
```

Restoring previously saved states:
```json
"state_preservation": {
  "action": "restore"
}
```

