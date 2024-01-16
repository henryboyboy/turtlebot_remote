# turtlebot remote

## Setup

### sourcing ROS

Add the following to your bashrc file for ros and the workspace to be sourced when opening a new terminal in dev_ws. make sure your are not sourcing ROS in your bashrc file.


```bash
if [ -f "/dev_ws/setup.bash" ]; then
    source /dev_ws/setup.bash
fi
```

## use

### build the image

Running the following command from the root of the repo will execute the build image shell script

```bash
.docker/build_image.sh
```

### run the image

Running the following command from the root of the repo will execute the run image shell script

```bash
.docker/run_user.sh
```

with Nvidia support (requires nvidia-docker2)

```bash
.docker/run_user_nvidia.sh
```
Once inside the container, ake ownership of the workspace with

```
sudo chown -R $USER /dev_ws
```
### Terminal(turtlebot nuc)
```bash
ssh iaac@10.41.1.1
cd turtlebot_robot
.docker/run_user.sh
roslaunch turtlebot_bringup iaac.launch
```

### Terminal2(turtlebot_remote Local)
```bash
cd turtlebot_remote
.docker/run_user.sh
sudo chown -R YOURUSER /dev_ws
terminator
```
### Terminator(Docker image)
##Mapping
1. To launch the robot in rviz
```bash
rviz
```

2. Launch gamapping
```bash
roslaunch turtlebot_navigation turtlebot_gmapping.launch
```
3. Teleoperation
```bash
roslaunch turtlebot_teleop keyboard_teleop.launch
```
4 To sav map 
```bash
rosrun map_server map_saver -f /dev_ws/src/turtlebot_apps/turtlebot_navigation/maps/<name>
```
##Navigation
1. Change the map name in amcl_demo_iaac.launch
2. Rviz(load the config)
3. Launch the navigation node
```bash
roslaunch turtlebot_navigation amcl_demo_iaac.launch
```
4. Find the estimate pose
5. Navigate to the target

