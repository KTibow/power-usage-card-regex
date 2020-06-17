[![hacs_badge](https://img.shields.io/badge/HACS-Custom-orange.svg)](https://github.com/custom-components/hacs)
# Lovelace power usage graph card with regexp

This card will display a doughnut chard that gives insights in your current power usage. Unlike the original one, you don't need to enumerate all the devices you have - you just need to define a regular expression matching all the entities. 

Note: the card is not collecting any data, it is only displaying momentary values. If your devices report "power" (in Watt) and not "power usage" (kWh, sometimes Ws), then you should consider using "integration" (https://www.home-assistant.io/integrations/integration/) or "utility meter" (https://www.home-assistant.io/integrations/utility_meter/) components.

The card will suppress displaying entities which do not have a numeric state (normally "unavailable", on devices which are really unavailable or just not initialized yet).

## Usage
1. 
- HACS: add through HACS. You will likely need to have HACS include this plugin into the Lovelace ressources and to reload the page after it
- manual:
Add plugin .js as a module:
```
- url: /local/power-usage-card-regex.js
  type: module
```
2. Add lovelace card to view:
```
- type: "custom:power-usage-card-regex"               # Mandatory
  title: "Power consumption"                       # Optional customized title
  total_power_usage: sensor.power_consumption      # Optional total power consumption (DSMR) sensor.
                                                   # If available then other measured values will be 
                                                   # substracted from total to calculate 'unknown' value.
  unknownText: "Total"                             # Optional customized unknown text. Only applicable
                                                   # with total_power_usage option enabled.
  filter: "^.*_total$"                             # Mandatory - regular expression to match; 
                                                   #    all entities matching this RE will be treated
                                                   #    as included, if they have a numeric state;
                                                   #    their name will be taken from "friendly_name" attribute,
                                                   ä    so set them wisely
 ```

![screenshot](https://raw.githubusercontent.com/DBa2016/power-usage-card-regex/master/power-usage-card-regex.png)
