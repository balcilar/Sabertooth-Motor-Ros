
# Drive Sabertooth Motor by Arduino using ROS

This project is for driving custom 4-wheeled robot motors (with front steering via Stepper Motor + rear wheel drive with DC motor) by Arduino with ROS Twist cmd_vel messages. The rear wheel drive gets controlled via Arduino and a Sabertooth Motor Controller from Dimension Engineering. The front steering is controlled via a stepper motor driver. Sabertooth motor controlled by pin 11 which defined by first com posrts TX under 9600 baud rate, ROS keep communicate by second com port whose port is 0 and 1 as default as 57600 baud rate. 

## How to Run

* Install rosserial-ardunio with following commands that could be done one time in your machine.
Note my ros is kinetic, so if your ros is for instance indigo, you should type indigo instead of kinetic
and also note my catkin workspace name is catkin_ws and it is ~/catkin_ws folder 
```
$ sudo apt-get install ros-kinetic-rosserial-arduino
$ sudo apt-get install ros-kinetic-rosserial
$ sudo apt-get install ros-kinetic-teleop-twist-keyboard
$ cd ~/catkin_ws/src
$ git clone https://github.com/ros-drivers/rosserial.git
$ cd ..
$ catkin_make
$ cd ~/Arduino
$ rosrun rosserial_arduino make_libraries.py .
```
* Downlaod Sabertooth driver from https://www.dimensionengineering.com/info/arduino link into library folder in Ardunio folder

* Downlaod this folder into your Ardunio folder

* Open Arduino IDE, open ros_drive.ino project and load that code into your arduino

* Check in which com port your arduino connected by clicking Arduino IDE->Tool->Port. For example in my machine it is /dev/ttyACM1, it could be ttyUSB0,1,2 or ACM0,1,2.

* in first terminal run roscore with following command.
```
$ roscore
```
in second terminal run rosserial to let the ros connect your arduino (pay attention to your port name)
```
$ rosrun rosserial_python serial_node.py /dev/ttyACM1 _baud:=57600
```

in third terminal open keyboard teleoperator. this teleoperator send ros messages to ros network
```
$ rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```

Now use this keys
* i : forward
* , : backward
* k : left
* j : right

and also you can sue 
* o : both forward and right
* u : both forward and left 
* . : both backward and right
* m : both backward and left 





