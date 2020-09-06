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
- Most of the times in a real world setting, the robot would have neither a map nor know its pose to localize itself in the environment i.e to know about the mapping of the environment, and this is where SLAM comes in. With SLAM, the robot does an outstanding job with just its own movement and sensory data to build a map of its environment while simultaneously localizing itself relative to building map.
- SLAM has two key approaches -
   - Grid-based FastSLAM
   - GraphSLAM

- RTAB-MAP - Real-Time Appearance-Based Mapping(RTAB-Map) is an RGB-D Graph-Based SLAM approach based on an incremental appearance-based loop closure detector. For this project, RTAB-MAP is used, and it is composed of Front-end and Back-end.
- In general, GraphSLAM has a better accuracy over FastSLAM unlike using particles at a location in the environment, GraphSLAM works with all the data at once to find the optimal solution. So, the project focuses on using GraphSLAM for the task at hand.
- `Front end` - The Front-end of GraphSLAM looks at how to construct the graph using the odometry and sensory measurements collected by the robot. This includes interpreting sensory data, creating the graph, and continuing to add nodes and edges to it as the robot traverses the environment.
- `Back end` - The Back-end of GraphSLAM is where the magic happens. The input to the Back-end is the completed graph with all of the constraints. And the output is the most probable configuration of robot poses and map features. The back-end is an optimization process that takes all of the constraints and finds the system configuration that produces the smallest error. It is a lot more consistent across applications.
- For this project, the Front-end and Back-end are performed iteratively, with a Back-end feeding an updated graph to the Front-end for further processing.
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
$ roslaunch my_robot amcl.launch
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
## Mapping Mode
Launching mapping `roslaunch my_robot mapping.launch` then navigate using `teleop` for map generation

<p align ="center">
<img src="https://github.com/ashutoshtiwari13/Map-a-world-with-SLAM/blob/master/output/Overview.png" height= "500px" width="800px"/>
</p>

### Localization Mode
A localization project using ROS AMCL package to accurately localize a mobile robot inside a map in the Gazebo simulation environments.

<img src="https://github.com/ashutoshtiwari13/Map-a-world-with-SLAM/blob/master/output/localization.gif" height="425px" width="400px" hspace="20"/><img src="https://github.com/ashutoshtiwari13/Map-a-world-with-SLAM/blob/master/output/localization_2.gif" height="425px" width="400px"/>


<img src="https://github.com/ashutoshtiwari13/Map-a-world-with-SLAM/blob/master/output/local_4.gif" height="425px" width="400px" hspace="20"/><img src="https://github.com/ashutoshtiwari13/Map-a-world-with-SLAM/blob/master/output/local_4.gif" height="425px" width="400px"/>
