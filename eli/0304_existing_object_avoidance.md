# Current ArduPilot Object Avoidance Background

# Overview

Currently Ardupilot offers several kinds of object avoidance for objects, ground, and ceilings. There is also avoidance of other Airborne Vehicles available (ADSB). All these methods require external hardware.

# Hardware Possibilities

In the current repo, ardupilot is capable of detecting objects through proximity sensors, range finders, and realsense depth cameras. 

# Simple Object Avoidance

For rovers which is the purpose of this project, simple object avoidance is only capable of stopping when detecting an object. It is not able to plan a path around the objects it encounters. A range of hardware can be used including lidar, and rangefinders.
Other sensors that are capable of providng MAVLink messages can also be used.

## Setup - 
* set AVOID_ENABLE = "7" - this enables all sources of barrier information to be used.
* set PRX1_TYPE = "4" to enable use of first range finder as a proximity sensor.


# BendyRuler - Path Planning
The BendyRuler algorithm searches in various directions around the vehicle for open areas, aiming to choose a path that is adequately clear and also guides the vehicle towards its ultimate goal.

## Setup - 
* set OA_TYPE = 1 - this enables the bendyruler algorithm
* set OA_BR_LOOKAHEAD - Distance ahead of the vehicle that needs to be probed. Obstacles further away than this will not be considered. General advice is that this distance needs to be long enough that paths around the obstacles can be seen, but not that long that it is detecting objects further than necessary.
* set OA_MARGIN_MAX - Distance the vehicle should stay away from objects with 2m being standard.
* set OA_BR_TYPE - choice of horizontal or vertical pathing. "1" is required setting for horizontal pathing. 

# Dijkstras

Internally builds up safe areas calculated from stay-out zones and finds the shortest path to the destination.
