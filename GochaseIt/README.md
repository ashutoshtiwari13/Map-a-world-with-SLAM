### Chase the Ball - Go Chase it

A mini-project build as a part of major SLAM project which uses ROS and Gazebo to build a mobile robot for chasing a white ball.

![chase]()

## Project Heads Up
- `my_robot`: This package defines the world and the robot.

- `ball_chaser`: This package contains two ROS nodes for commanding the robot to chase the white ball.

## Setup

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

5. See the project scenario using
```sh
$ roslaunch my_robot world.launch
```

6. Open another terminal ``(Ctrl+Shift+T)``, and launch the `ball_chaser` package
```sh
$ source devel/setup.bash
$ roslaunch ball_chaser ball_chaser.launch
```
Pick up the ball and place infront of the mobile robot, the robot shall follow!
