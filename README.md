# Lovelace power usage graph card

This card will display a doughnut chard that gives insights in your current power usage. 

## Usage
1. Add plugin .js as a module:
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
                                                   #    as included, if they have a numeric state
 ```

![screenshot](https://raw.githubusercontent.com/DBa2016/power-usage-card-regex/master/power-usage-card-regex.png)
