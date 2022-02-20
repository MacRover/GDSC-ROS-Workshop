# Pre-workshop installation

1. Run command prompt or powershell as administrator.

2. Type `wsl --install -d Ubuntu-18.04` and press enter. Windows will download and install 
the Ubuntu 18.04 WSL system. This process can take a while depending on your internet 
speed.

3. When the process is complete a new window will appear. Wait for the installation to finish, 
and then follow the instructions to configure a new UNIX user for your WSL install. Select 
any username or password (does not need to match your windows account).

4. After configuring your new account, you will be presented with a terminal prompt. Type 
`sudo apt update && sudo apt upgrade -y`. Input the password you made in the last step 
and press enter (you will not see your password appear as you type it).

5. Type: `sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) 
main" > /etc/apt/sources.list.d/ros-latest.list'` and press enter.

6. Type: `curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | 
sudo apt-key add -` and press enter. Command should return OK.

7. Type: `sudo apt update && sudo apt install ros-melodic-desktop-full ros-melodic-turtlebot3 ros-melodic-turtlebot3-simulations ros-melodic-gmapping python-rosdep python-rosinstall python-rosinstall-generator python-wstool build-essential x11-apps gnome-terminal -y` and press enter. If you're running Ubuntu 20.04, replace all instances of `melodic` in this command with `noetic`.

8. Type: `echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc && source ~/.bashrc`
and press enter.

For installing on a Linux computer, open a terminal prompt, start at step 5, and follow the same instructions. If you're using a Raspberry Pi, check out this guide: http://wiki.ros.org/ROSberryPi/Installing%20ROS%20Melodic%20on%20the%20Raspberry%20Pi

# Demo 1

The following are the basic commands that are shown in the first demo:

## 1. This command launches the ROS master:

```
roscore
```


## 2. This command launches a node:

Usage: 

```
rosrun [package_name] [node_name]
```
Example: 
```
rosrun turtlesim turtlesim_node
```


## 3. This command list all the current topics:

```
rostopic list
```


## 4. This command provides more information about a topic:

Usage: 

```
rostopic info [topic]
```
Example: 
```
rostopic info /rosout
```

## 5. This command provides more information about a message:

Usage: 

```
rosmsg info [msg]
```
Example: 
```
rosmsg info std_msgs/Bool
```

## 6. This command publishes data:

Usage:

```
rostopic pub [topic] [msg_type] [args]
```

Use `-r` to publish every 2 seconds

Example"

```
 rostopic pub /testtopic std_msgs/String -- "Hello" -r 2
```

## 7. This command subscribes to a topic and echoes the data:

Usage:

```
rostopic echo [topic]
```

Example"

```
 rostopic echo /testtopic
```

## 8. This command visualizes your current ROS system:

```
rosrun rqt_graph rqt_graph
```

# Interactive Demo

## Step 1:
Open up a terminal window (on Windows 11 search for 'Ubuntu')

## Step 2: Assigning enviornment variables (specific to this example)
Type: `echo "export TURTLEBOT3_MODEL=waffle" >> ~/.bashrc && source ~/.bashrc`
(This is to set up the enviornment variables for the robot to use in this example)

## Step 3: Setting up terminal enviornment
Open up 3 more terminal windows (you should now have 4 total)
Arrange them so they take together take 1/4 of the screen (leaving 3/4 for other stuff)
***If you have a small screen you can open up `gnome-terminal` and open multiple tabs with `File -> New Tab` instead of multiple windows

## Step 4: Spawning in and driving a turtlebot
Terminal Window 1: `roslaunch turtlebot3_gazebo turtlebot3_world.launch`
Wait for gazebo to launch and resize it to fit in the top right corner of your screen

Terminal Window 2: `roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch`
try driving the robot around using the keyboard

## Step 5: Visualizing Sensor Data
Terminal Window 3: `roslaunch turtlebot3_gazebo turtlebot3_gazebo_rviz.launch`

## Step 6: SLAM (Simultaneous Localization and Mapping)
#### Close the terminal window in Step 5 and in a new one type:
`roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping`




