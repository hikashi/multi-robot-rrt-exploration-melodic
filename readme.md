# Multirobot Turtlebot3 Explore Unknown Environment Simulation based on RRT Exploration for Ubuntu 18.04 ROS Melodic
This package is a compilation of the RRT package in a much complete package rather than figuring map merging and other functions from other resipotary. 
This would serve as a self-contained package for the exploration module using simulation for the turtlebot.
This is tested on Ubuntu 18.04LTS with ROS Melodic.

credit to Hasauino for creating the RRT exploration packages.

[RRT Exploration package](https://github.com/hasauino/rrt_exploration "RRT Exploration").

[RRT Exploration Tutorial package](https://github.com/hasauino/rrt_exploration_tutorials "RRT Exploration").


An example of the video running RRT Exploration is shown below:

[RRT Exploration for Ubuntu 18.04 ROS Melodic](https://www.youtube.com/watch?v=2VntIlG6zmE  "RRT Exploration").

[![RRT Exploration for Ubuntu 18.04 ROS Melodic](https://img.youtube.com/vi/2VntIlG6zmE/0.jpg)](https://www.youtube.com/watch?v=2VntIlG6zmE "RRT Exploration for Ubuntu 18.04 ROS Melodic")



## Requirements
The following code is executed in ROS Melodic in Ubuntu 18.04 LTS

The following libraries are required to be installed before proceeding to run the code

    $ sudo apt-get install ros-melodic-gmapping
    $ sudo apt-get install ros-melodic-navigation
    $ sudo apt-get install python-opencv
    $ sudo apt-get install python-numpy
    $ sudo apt-get install python-scikits-learn
    $ sudo apt-get install ros-melodic-teb-local-planner


## Installation Process
Create a new folder called "catkin_explore/src" by executing the following comment:

    $ sudo mkdir -p ~/catkin_explore/src
    $ cd ~/catkin_explore/src/
    $ git clone https://github.com/hikashi/multi-robot-rrt-exploration-melodic.git
    $ cd ~/catkin_explore
    $ catkin_make

## Add in Amazon Map (OPTIONAL)
Download the Amazon world map by executing the following comments:

    $ cd ~/catkin_explore/src
    $ git clone https://github.com/aws-robotics/aws-robomaker-small-house-world.git
    $ git clone https://github.com/aws-robotics/aws-robomaker-bookstore-world.git
    $ cd ~/catkin_explore/
    $ catkin_make
    

## Execution for Single Robot
The program can be executed using the following comments in three different terminals:

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
The program can be executed using the following comments in three different terminals:

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
The exploration starts by relying on the correct sequence of punching in points for the exploration boundary. This can be achieved by inputting the clicked point in the following sequence:
1. Top Left
2. Bottom Left
3. Bottom Right
4. Top Right
5. Initial Point
 ![Instruction](/instruction2.png)
 Things to note: 5th initial point should be within the known map or preferably close to the robot starting point. 
 
 
## Saving Map
Save the map using the following command:

    # rosrun map_server map_saver -f mymap
    
## How to speed up Gazebo
- Try to download the [online models](https://github.com/osrf/gazebo_models) and put inside "~/.gazebo/models/" folder 
- Try not to run a lot processes in the background (simulation is CPU intensive)
- RVIZ might take up some of the computing power, can try to drop some topics if needed.

## known issues
1. The map merging will shift a lot if the slam drifting is too severe.
2. Shifting causes the frontier point to remain even after being explored.
3. Sometimes robots will take some time to move to a new plan.
4. The revenue function is awkwardly computing large negative value and hence the navigation cost seems insignificant. (inherited from the original RRT exploration)
5.  The assignment of the goal is not close to suboptimal. May need to perform optimization on the goal allocation.
