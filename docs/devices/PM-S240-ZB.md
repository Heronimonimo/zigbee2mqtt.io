---
title: "Dawon DNS PM-S240-ZB control via MQTT"
description: "Integrate your Dawon DNS PM-S240-ZB via Zigbee2mqtt with whatever smart home
 infrastructure you are using without the vendors bridge or gateway."
---

*To contribute to this page, edit the following
[file](https://github.com/Koenkk/zigbee2mqtt.io/blob/master/docs/devices/PM-S240-ZB.md)*

# Dawon DNS PM-S240-ZB

| Model | PM-S240-ZB  |
| Vendor  | Dawon DNS  |
| Description | IOT smart switch 2 gang |
| Supports | on/off |
| Picture | ![Dawon DNS PM-S240-ZB](../images/devices/PM-S240-ZB.jpg) |

## Notes


### Routing functionallity
This device does **not** act as a router.


## Manual Home Assistant configuration
Although Home Assistant integration through [MQTT discovery](../integration/home_assistant) is preferred,
manual integration is possible with the following configuration:


{% raw %}
```yaml
switch:
  - platform: "mqtt"
    state_topic: "zigbee2mqtt/<FRIENDLY_NAME>"
    availability_topic: "zigbee2mqtt/bridge/state"
    payload_off: "OFF"
    payload_on: "ON"
    value_template: "{{ value_json.state_top }}"
    command_topic: "zigbee2mqtt/<FRIENDLY_NAME>/top/set"

switch:
  - platform: "mqtt"
    state_topic: "zigbee2mqtt/<FRIENDLY_NAME>"
    availability_topic: "zigbee2mqtt/bridge/state"
    payload_off: "OFF"
    payload_on: "ON"
    value_template: "{{ value_json.state_bottom }}"
    command_topic: "zigbee2mqtt/<FRIENDLY_NAME>/bottom/set"

sensor:
  - platform: "mqtt"
    state_topic: "zigbee2mqtt/<FRIENDLY_NAME>"
    availability_topic: "zigbee2mqtt/bridge/state"
    icon: "mdi:signal"
    unit_of_measurement: "lqi"
    value_template: "{{ value_json.linkquality }}"
```
{% endraw %}


