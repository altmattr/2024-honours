# Current ArduPilot Following 

# Background

In the current follow mode, the vehicle (in this case, a rover) will try to follow another vehicle or object that is transmitting its current position. 

# Basic Solution

The current basic solution is that each vehicle has a telemetry radio and shares the same NetID, and vehicle B just follows vehicle A using the information from the radio.

![Follow1](https://github.com/altmattr/2024-honours/assets/80295061/4e8a072f-9c24-41c1-8a23-c145e24b27a2)

# Advanced Solution

The advanced solution will most likely be the one that is focused on as it uses a Ground Control Station (GCS). A second telemetry radio is required on whichever vehicle needs to be connected.

![Follow2](https://github.com/altmattr/2024-honours/assets/80295061/955f3978-be3c-47d7-b205-6b4c8f743ce8)

#Follow Mode Parameters

`FOLL_ENABLE` set to 1 to enable follow mode and refresh parameters.

`FOLL_SYSID` MAVLink system id of lead vehicle (“0” means follow the first vehicle “seen”).

`FOLL_DIST_MAX` if lead vehicle is more than this many meters away, give up on following and hold position (loiter if boat, stop if ground vehicle).

`FOLL_OFS_X, FOLL_OFS_Y, FOLL_OFS_Z (not used in Rover)` 3D offset (in meters) from the lead vehicle. If they are zero, then the current vehicle’s offset from the follow target at time of mode entry is used every time. These offsets can be altered via Mavlink and will take effect immediately. However, if they were originally zero and changed during FOLLOW MODE rather than during another mode, they will be reset to zero for the next entry into FOLLOW mode, until a reboot occurs and then the changed offsets will be restored.

`FOLL_OFS_TYPE` set to 0 if offsets are North-East (NED), 1 if offsets are relative to lead vehicle’s heading, see diagrams below.

`FOLL_POS_P` gain which controls how aggressively this vehicle moves towards lead vehicle (limited by WPNAV_SPEED)

# Telemetry Radios 

Telemetry radios provide this information:

Real-time Data Transmission: They allow for the real-time transmission of movement data, including altitude, speed, GPS coordinates, and system status, from the vehicle to vehicle or to the ground control station. This information is vital for monitoring the vehicle's status and performance during movement or navigation.

Command and Control: Beyond just sending data back to the operator, telemetry radios can be used to send commands from the GCS to the vehicle. This includes changes in direction, altitude, speed, and other operational parameters, allowing for dynamic control of the vehicle based on real-time data.

Enhanced Safety: By providing real-time data transmission, telemetry radios enhance the safety of unmanned vehicle operations. Operators can monitor system health, battery status, and environmental conditions, making informed decisions to prevent accidents or mishaps.

Range and Reliability: These radios are designed to operate over long distances, from 300 metres out of box to potentially several of kilometers, depending on the technology and setup. They offer reliable communication even in challenging environments or where direct line of sight is not possible.

# Ground Control Stations

Ground Control Stations (GCS) serve as crucial interfaces for controlling drones, UAVs, and other unmanned systems, offering a blend of hardware and software components designed for comprehensive mission management. These stations allow operators to command their vehicles, plan missions, monitor real-time data, and even control UAVs directly through a "virtual cockpit" interface that mirrors the experience of piloting an aircraft.

The selection of a GCS can depend on several factors, including the specific vehicle being operated and the user's preferred computing platform. Desktop applications like Mission Planner and QGroundControl are popular among DIY enthusiasts and developers for their extensive configuration and analysis tools. At the same time, mobile apps provide portability and ease of use for on-the-go operations. Code developers might lean towards MAVProxy for its specialized features and extensibility.

# Evidence 

https://ardupilot.org/rover/docs/follow-mode.html
https://ardupilot.org/copter/docs/common-sik-telemetry-radio.html
https://en.wikipedia.org/wiki/Telemetry
https://ardupilot.org/rover/docs/common-choosing-a-ground-station.html
