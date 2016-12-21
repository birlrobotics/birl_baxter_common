# birl_baxter_common

# Purpose
This package is used for applying Baxter robot from rethink robotics inc to experiments of our lab,BIRL.
The package is of the extension from baxter_common,a package from baxter sdk.

# New Feature

![baxter](https://github.com/birlrobotics/birl_baxter_common/blob/master/media/baxter.png)

The environment for BIRL includes as followed:
  1.  Asus xtion camera sensor and camera frame
  2. Table
  3. Force torque sensor and its design
  4. camera gripper and holder designed for camera snap assembly task
  5. some object model for task

For more detail, you can click [New Feature documentation](https://github.com/birlrobotics/birl_baxter_common/wiki/New-Features-documentation)

# Dependence
This package depend on baxter_common,baxter_simulator.So you must install [baxter_sdk](http://sdk.rethinkrobotics.com/wiki/Workstation_Setup) and [baxter_simulator](http://sdk.rethinkrobotics.com/wiki/Simulator_Installation).make sure you instatll baxter_sdk and baxter_simulator properly.

# Installation
1.First of all you should install 
- [baxter_sdk](http://sdk.rethinkrobotics.com/wiki/Workstation_Setup) 
- [baxter_simulator](http://sdk.rethinkrobotics.com/wiki/Simulator_Installation).

  Please follow the installation wiki on rethink robotics official website  

  you can try this to check if your baxter gazebo environment is setup well
````
roslaunch baxter_gazebo baxter_launch 
```` 
 
2.Install the repo birl_baxter_common and birl_baxter_simulator
````
cd {your_baxter_work_space}/src 
  (got to your baxter_ws,in my case, cd ~/ros/indigo/baxter_ws/src)
git clone https://github.com/birlrobotics/birl_baxter_common.git
git clone https://github.com/birlrobotics/birl_baxter_simulator.git
cd ..
catkin_make
````
finish  installing, enjoy!

# Launch examples
For the box assembly task with baxter
````
roslaunch birl_sim_examples pa_box_gazebo.launch
````
or 
````
roslaunch birl_baxter_description pa_box_gazebo.launch
roslaunch birl_sim_examples pa_box.py
````

For the snap assembly task with baxter
````
roslaunch birl_sim_examples pa_snap_gazebo.launch
````
or 
````
roslaunch birl_baxter_description pa_snap_gazebo.launch
roslaunch birl_sim_examples pa_box.py
````

# Mechanical design source
Here are the repo which contain our mechanical design source[birl_baxter_hands](https://github.com/birlrobotics/birl_baxter_hands)

# Learn more about BIRL
Welcome to [BIRL](https://github.com/birlrobotics/birl_baxter/wiki)
