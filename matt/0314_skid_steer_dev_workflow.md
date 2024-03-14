# Aim

Get a decent dev setup working for making ardupilot changes and testing them

# Failed attempts

I like to use mission planner, but the dev workflow is terrible.  You can only run simulations with cygwin binaries which means you need to build in cygwin, then you copy the executable over to some place, restart mission planner, start a new sim, then test - all by hand.  I tried it, it just didn't work.

# Current attempt

MavProxy does a good simulation and can be run in a docker container as long as you tunnel your x11 forwarding through.  I am documenting this process here partly because I have been able to turn an unarmed rover in my testing.  I want a minimal way to replicate this error. 

# Pre-reqs
  * git
  * docker
  * xming/xquartz

# Steps
  * Clone repo (recursively clone submodules)
  * Add devcontainer config
    * Existing Docker
    * Add SSH
  * Reopen in container
  * wait
  * get console in container
  * > cd Rover
  * > ../Tools/autotest/sim_vehicle.py
  * wait, oh lordy we have to wait