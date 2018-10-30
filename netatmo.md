# Plugin Netatmo for Hass

## General structuration
![alt text](https://github.com/Moumoustache/Hass/blob/master/Structuration.png "netatmo")

## EndPoints used :
Homesdata (HD)
```https://api.netatmo.com/api/homesdata```

Homestatus (HS)
```https://api.netatmo.com/api/homestatus```

## Step
1- Call homesdata to get home/rooms/modules structuration by looping on every entities. Are expected only NATherm1 (thermostat)and NRV (valve) for modules

2- Once all entities are prepared Call homestatus and get information per home, per room and per module

3- add it to hass :)

## Home structure
From HS:
* id
From HD:
* id
* name

## Rooms structure
From HS:
* id
* therm_measured_temperature 
  * defintion : actual temperature in the room
  * example : 22.4
* therm_setpoint_temperature
  * defintion : target temperature in the room
  * example : 18
* therm_setpoint_mode
  * defintion : actual mode
  * value : manual, max, off, schedule, away, hg
  * example : manual
* reachable
  * definition : is there at least one module of the room reachable
  * value : true, false
  * example : true
From HD:
* id
* name
* type
  * defintion : type of module
  * value : kitchen , bedroom, livingroom, bathroom, lobby, custom, outdoor, toilets, garage, home_office, dining_room, Corridor, stairs
  * example : kitchen

## Modules structure
From HS:
* id
* reachable
  * defintion : is connected or not
  * example : 22.4
* therm_setpoint_temperature
  * defintion : target temperature in the room
  * example : 18
* therm_setpoint_mode: "schedule"
  * defintion : actual mode
  * value : manual, max, off, schedule, away, hg
  * example : manual
From HS:
* id
* reachable
  * definition : is the module reachable
  * value : true, false
  * example : true
* rf_strength
  * definition: radio strength
  * value: 90 = low, 80 = medium, 70 = high, 60 = full signal
* battery_state
  * definition : state of the battery
  * value: full, high, medium, low
* boiler_status (only if the module is ```type: NATHERM1```)
  * definition: is the boiler active or not
  * value: true, false
  * example : true
* boiler_valve_comfort_boost
  * definition: is a valve controlling the boiler
  * value: true, false
  * example : true
From HD:
* name
* type
  * defintion : type of module
  * value : NATherm1 (thermostat), NRV (valve), NAPlug (relay)
  * example : NRV
  

