# Overview - Current ArduPilot Object Avoidance Background

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
![Screenshot 2024-03-17 at 1 48 10 pm](https://github.com/altmattr/2024-honours/assets/91449994/2cf3bf97-3f50-4dfd-b5a9-96a378d84cb6)



## Setup - 
* set OA_TYPE = 1 - this enables the bendyruler algorithm
* set OA_BR_LOOKAHEAD - Distance ahead of the vehicle that needs to be probed. Obstacles further away than this will not be considered. General advice is that this distance needs to be long enough that paths around the obstacles can be seen, but not that long that it is detecting objects further than necessary.
* set OA_MARGIN_MAX - Distance the vehicle should stay away from objects with 2m being standard.
* set OA_BR_TYPE - choice of horizontal or vertical pathing. "1" is required setting for horizontal pathing. 

# Dijkstras - Path Planning

Internally builds up safe areas calculated from stay-out zones and finds the shortest path to the destination.
![Screenshot 2024-03-17 at 1 35 55 pm](https://github.com/altmattr/2024-honours/assets/91449994/1dbc4089-d619-4ad0-b933-4cb258f63053)

## Setup - 
* set OA_TYPE = 2 - this enables dijkstra's algorithm
* set OA_MARGIN_MAX - Distance the vehicle should stay away from objects with 2m being standard.
* set OA_OPTIONS - can be set to use S-Curves around fence corners in the planned path to speed up turns.

# Combined Dijkstras & BendyRuler - Path Planning

Begins with traditional Dijkstra's planning of the shortest path, if it comes axcross a proximity based obstacle the navigation would switch to BendyRuler.

## Setup - 
* OA_TYPE = 3

# References
* https://ardupilot.org/copter/docs/common-oa-dijkstrabendyruler.html
* https://ardupilot.org/copter/docs/common-oa-dijkstras.html
* https://ardupilot.org/copter/docs/common-oa-bendyruler.html
* https://ardupilot.org/copter/docs/common-simple-object-avoidance.html
* https://ardupilot.org/copter/docs/common-object-avoidance-landing-page.html
