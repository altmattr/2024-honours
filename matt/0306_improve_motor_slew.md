# Improving motor slew for skid steer rovers/boats

# Background

"Motor slew" is the characteristic of a motor where is spins up slowly even when full throttle is applied.  This can be a property of the motor itself or it can be in the speed controller or it can be simulated in software.

ArduPilot Rover has a motor slew parameter [`MOT_SLEWRATE`](https://ardupilot.org/rover/docs/parameters.html#mot-slewrate) to support software simulated motor slew.

## Problem

In Ardupilot Rover motor slew is applied to throttle output but it is possible to configure ArduPilot rover so that motors are also used for steering (skid steering mode).  In this case, the simulated slew is not applied to the motors when it is turning inputs that are causing signals to go to the motors and the motors react very quickly.

### Notes
  * The problem is hidden in auto modes because in those modes the controllers tend to increase all parameters slowly already and fast changes to inputs are unlikely.
  * The problem is pronounced in manual mode becuase a user applying joystick inputs can go full left or full right very easily.

### Evidence
  * https://discuss.ardupilot.org/t/mot-slew-rate-limit-not-properly-applied-to-motor-outputs/98444
  * https://discuss.ardupilot.org/t/slew-rates-on-servo-output/84694/7

## Proposed Solution

Adjust the ArduPilot code to apply `MOT_SLEWRATE` at the motor output rather than at the throttle calculation as it currently is.

### Steps
  * Replicate the problem in simulation
    * Skid-steer rover simulation
  * Adjust ArduPilot Code
     * ArduPilot development environment
       * ArduPilot dev on CodeSpaces
       * Run my own build in the simulation
      *  ~~Find the code in question~~
  * Test in simulation
    * Design the test.
  * Test in real life

## Details


```mermaid
graph TD;
    output --> output_regular;
    output --> output_skid_steering;
    output <--> slew_limit_throttle;
    output_regular --> output_throttle;
    output_skid_steering --> output_throttle;
    output_throttle --> get_scaled_throttle;
    output_throttle --> get_rate_controlled_throttle;
```
  * `output` is the overall function to output throttle and steering.  It adjusts the throttle value _at this point_ for slew using the helper `slew_limit_throttle` function.
  * `output_skid_steering` is responsible for adding the steering adjusments to the throttle values so that the throttles can give effect to direction change.
  * `get_scaled_throttle` applies the throttle curve if one is defined
  * `get_rate_controlled_throttle` applies the turn rate controller to the skid steer throttle outputs.  This feels like it might substitute for slew but it only works in various auto modes.  You can see that is checked int he code (the adjustment is guarded by `A && _rate_controller.enabled(0)) `)

### Comments

I would like to know the logic for applying the slew limit in a different place to the throttle curve and the turn rate controls.  I think putting slew limit into that pipeline all the way down at `output_throttle` makes more sense.
# WIP

`mode.cpp` calculates `throttle_out_limited` using a `g2.motors` function `get_slew_limited_throttle`.  In this function, `_slew_rate` local variable is used to adjust the planned throttle change (`dt`) according to the slew rate.

`AP_MotorsUGV::slew_limit_throttle` also uses this function to calculate the next throttle value.

All of this eventually gets sent to `output_throttle`.  If it goes via standard steering it goes directly (and I assume is based on _throttle).  If it goes via skid steering then the `steering_scaled` is added and this has no motor slew applied, even when `_throttle` has.

The connection between the parameter `MOT_SLEWRATE` and a variable in the code is done by an `AP_GROUPINFO` call in `AP_MotorsUGV.cpp`.  Here it is linked to the `_slew_rate` variable and defaults to `100`.  Here it is called only `SLEWRATE`, I've not found where the `MOT_` gets appended.