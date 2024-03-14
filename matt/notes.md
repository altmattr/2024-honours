# What did I have to do to get the cygwin build to work

The symbolic links needed to be to python3 and pip3 

I had to use python3 -m pip install 

I had to install one extra pip package (penable?)

Then it seemed to work.

At this point you copy follow the other instruction

./waf configure --board sitl --toolchain=i686-pc-cygwin
./waf vehicle where vehicle is copter, plane, heli …

move the *.exe file that is located in the cygwin64\home<user>\ardupilot\build\sitl\bin directory to your documents\mission planner\sitl directory
Then to keep mission planner from downloading the file make sure you select the “skip download”