## Mapping a World using SLAM

This project is about implementing SLAM(Simultaneous Localization and mapping) with RTAB-MAP(Real-Time Appearance-Base Mapping) package. Two 2D occupancy grid and a 3D octomap is created from a simulated environment.

**Note** : A mini-project for this project can be found in the `GoChaseit` directory [here](https://github.com/ashutoshtiwari13/Map-a-world-with-SLAM/tree/master/GochaseIt)

<p align ="center">
<img src="https://github.com/ashutoshtiwari13/Map-a-world-with-SLAM/blob/master/output/Overview.png" height= "500px" width="800px"/>
</p>

#### 1. [Project Heads Up](#Project-Heads-Up)
#### 2. [Setup](#Setup)
#### 3. [Mapping and Simulation](#Mapping-and-Simulation)

## Project Heads Up
- The robot configuration frames.The ROS tf library is used to keep track of all the different coordinate frames and defines their relation to one another. For this project the tf view_frames is used to create the graphical representation of the bot as shown below.

<p align ="center">
<img src="https://github.com/ashutoshtiwari13/Map-a-world-with-SLAM/blob/master/output/frames.png" height= "400px" width="900px"/>
</p>
- The world used in the project the default `Udacityoffice.world` provided by Udacity.

## Setup
### Prerequisites/Dependencies  
* Gazebo >= 7.0  
* ROS Kinetic  
* ROS navigation package  
```
sudo apt-get install ros-kinetic-navigation
```
* ROS map_server package  
```
sudo apt-get install ros-kinetic-map-server
```
* ROS move_base package  
```
sudo apt-get install ros-kinetic-move-base
```
* ROS amcl package  
```
sudo apt-get install ros-kinetic-amcl
```
* ROS rtabmap-ros package
```
sudo apt-get install ros-kinetic-rtabmap-ros
```
* make >= 4.1(mac, linux), 3.81(Windows)
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools](https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)

### Run the setup

1. Move to the `/src` directory of your active ROS workspace and clone the project files.
```sh
$ cd ~/catkin_ws/src
$ git clone https://github.com/ashutoshtiwari13/Map-a-world-with-SLAM.git
```
2. Install missing dependencies using rosdep install.
```sh
$ cd ~/catkin_ws
$ rosdep install --from-paths src --ignore-src --rosdistro=kinetic -y
```

3. Build the project.
```sh
$ cd ~/catkin_ws
$ catkin_make
```

4. Add following to your `.bashrc` file
```sh
$ source ~/catkin_ws/devel/setup.bash
```
Note : source the `~/.bashrc` file too to avoid errors.

5. Launch my_robot in Gazebo to load both the world and plugins
```sh
$ roslaunch my_robot world.launch
```
6. Launch teleop_twist_keyboard node, open a new terminal, enter  
```sh
$ cd ~/catkin_ws/
$ source devel/setup.bash
$ rosrun teleop_twist_keyboard teleop_twist_keyboard.py
$ roslaunch my_robot mapping.launch
```
6. Send move command via teleop package to control your robot and observe real-time visualization in the environment `rtabmapviz`.
```sh
$ rtabmap-databaseViewer ~/.ros/rtabmap.db
```
7. Once satisfied with your move, press `Ctrl + c` to exit then view your database with
```
rtabmap-databaseViewer ~/.ros/rtabmap.db
```

## Mapping and Simulation
