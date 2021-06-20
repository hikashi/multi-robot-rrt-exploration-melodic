# Multirobot Turtlebot3 Simulation Exploration based on RRT for Ubuntu 18.04 ROS Melodic
This package is a compilation of the RRT package in a much complete package rather than figuring map merging and other function from other resipotary. 
This would serve as a self-contained package for the exploration module using simulation for the turtlebot.
This is tested on Ubuntu 18.04LTS with ROS Melodic.

credit to hasauino for creating the RRT exploration packages.

[RRT Exploration package](https://github.com/hasauino/rrt_exploration "RRT Exploration").

[RRT Exploration Tutorial package](https://github.com/hasauino/rrt_exploration_tutorials "RRT Exploration").


## Requirements
The following code is exectuted in ROS Melodic in Ubuntu 18.04 LTS

The following libraries are required to install before proceeding to run the code

    $ sudo apt-get install ros-melodic-gmapping
    $ sudo apt-get install ros-melodic-navigation
    $ sudo apt-get install python-opencv
    $ sudo apt-get install python-numpy
    $ sudo apt-get install python-scikits-learn


## Installation Process
create a new folder called "catkin_explore/src" by executing the following comment:

    $ sudo mkdir -p ~/catkin_explore/src
    $ cd ~/catkin_explore/src/
    $ git clone https://github.com/hikashi/multi-robot-rrt-exploration-melodic.git
    $ cd ~/catkin_explore
    $ catkin_make


## Execution for Single Robot
The program can be executed using the following comments in three terminal:

Terminal 1

     # roscore 
Terminal 2

     # source ~/catkin_explore/devel/setup.bash 
     # export TURTLEBOT3_MODEL=waffle_pi
     # roslaunch ros_multitb3 single_tb3_house.launch
Terminal 3

     # source ~/catkin_explore/devel/setup.bash 
     # export TURTLEBOT3_MODEL=waffle_pi
     # roslaunch rrt_exploration single_tb3_exploration.launch 

## Execution for Multirobot
The program can be executed using the following comments in three terminal:

Terminal 1

     # roscore 
Terminal 2

     # source ~/catkin_explore/devel/setup.bash 
     # export TURTLEBOT3_MODEL=waffle_pi
     # roslaunch ros_multitb3 multi_tb3_house.launch 
Terminal 3

     # source ~/catkin_explore/devel/setup.bash 
     # export TURTLEBOT3_MODEL=waffle_pi
     # roslaunch rrt_exploration multi_tb3_exploration.launch 



## Exploration Process
The exploration relies on the correct sequence else rendering with no goal for each of the robot.
1. Top Left
2. Bottom Left
3. Bottom Right
4. Top Right
5. Initial Point


## Next milestone
- fix the collision avoidance and path planning of the move base
- add in more maps for the simulation
- modify the turtlebot to adapt different SLAM methods
