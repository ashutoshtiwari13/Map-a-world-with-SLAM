## Mapping a World using SLAM

This project is about implementing SLAM(Simultaneous Localization and mapping) with RTAB-MAP(Real-Time Appearance-Base Mapping) package. Two 2D occupancy grid and a 3D octomap is created from a simulated environment.
Note : A mini-project for this project can be found in the `GoChaseit` directory [here](https://github.com/ashutoshtiwari13/Map-a-world-with-SLAM/tree/master/GochaseIt)

<p align ="center">
<img src="https://github.com/ashutoshtiwari13/Map-a-world-with-SLAM/blob/master/output/Overview.png" height= "500px" width="800px"/>
</p>

### 1. [Project Heads Up](#Project-Heads-Up)
### 2. [Setup](#Setup)
### 3. [Mapping and Simulation](#Mapping-and-Simulation)

## Project Heads Up
-
- The robot configuration frames.The ROS tf library is used to keep track of all the different coordinate frames and defines their relation to one another. For this project the tf view_frames is used to create the graphical representation of the bot as shown below.

<p align ="center">
<img src="https://github.com/ashutoshtiwari13/Map-a-world-with-SLAM/blob/master/output/frames.png" height= "400px" width="900px"/>
</p>
- The world used in the project the default `Udacityoffice.world` provided by Udacity.
## Setup

## Mapping and Simulation
