# robotiq_ros

This repo holds source code for ROS (indigo).

# Prerequisites
1. Install Ros (indigo). See: [ROS indigo][]
2. Install Moveit and other dependencies.
```
sudo apt-get install ros-indigo-moveit ros-indigo-moveit-full-pr2 ros-indigo-soem ros-indigo-controller-manager ros-indigo-socketcan-bridge
```
3. Install UR packages.
```
sudo apt-get install ros-indigo-universal-robot
```
# Installation
1. Clone the repo into your workspace.
```
cd <YOUR WORKSPACE>/src/
git clone https://github.com/littleblakew/robotiq_ros.git
```
2. Compile the packages.
```
cd ..
catkin_make
```
3. Install robotiq_modbus_tcp. 
```
rosdep install robotiq_modbus_tcp 
```
4. Install force_torque_tools.
```
sudo apt-get install ros-indigo-force-torque-tools
```

# Configuration
1. Enter the robotiq_ros folder
2. Copy the rule "52-ftdi.rules" into "/etc/udev/rules.d"
```
sudo cp /robotiq_force_torque_sensor/udev/52-ftdi.rules /etc/udev/rules.d
```
3. Reconnect the usb of FT300.
4. Check the new name of device of FT300, which is supposed to be "/dev/ftdi_XXXXXXXX".
5. Replace the old name of device of FT300 in "/robotiq_force_torque_sensor/launch/ft_300.launch" with the new name of device of FT300.

# Usage
[Gripper]
```
rosrun robotiq_s_model_control SModelTcpNode.py 192.168.1.11 
rosrun robotiq_s_model_control SModelSimpleController.py 
```
[F/T Sensor]
```
roslaunch robotiq_force_torque_sensor ft_300.launch
```
[ROS indigo]: http://wiki.ros.org/indigo/Installation/Ubuntu

# Reference
1. https://github.com/ros-industrial/robotiq
2. https://github.com/ibaranov-cp/husky_UR_accessories
