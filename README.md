# birl_baxter_common

# Purpose

This package is application in simulator for Baxter from rethink robotics company. 

# New Features

![baxter](https://github.com/birlrobotics/birl_baxter_common/blob/master/media/full.png)

New features for baxter simulation environment compared to the default one:

  -  Asus xtion camera sensor and camera frame
  -  Experimental table
  -  WACOH force torque sensor and its design
  -  A in-house designed plastic camera gripper holder used for a camera snap assembly task

For more details, you can click: [New Feature documentation](https://github.com/birlrobotics/birl_baxter_simulator/wiki/New-Features-documentation)

# Dependencies

This package depends on baxter_common and baxter_simulator. So you must finish installation of [baxter_sdk](http://sdk.rethinkrobotics.com/wiki/Workstation_Setup) and [baxter_simulator](http://sdk.rethinkrobotics.com/wiki/Simulator_Installation).

# Installation
visit [Installation](https://github.com/birlrobotics/birl_baxter_simulator/wiki/Installation)

# Running Examples
visit [Running Examples](https://github.com/birlrobotics/birl_baxter_simulator/wiki/Running-Examples)


# Mechanical Design Source
To access the repo with the hardware design of the FT sensor, grippers, and objects, see: [birl_baxter_hands](https://github.com/birlrobotics/birl_baxter_hands)

# Learn More About BIRL
Our central baxter repository has more information about a variety of packages that we support: [BIRL Baxter](https://github.com/birlrobotics/birl_baxter/wiki)


# Overview



Baxter's URDF need to update when you make changes on the robot, for example you can add a extra force sensor on the the end-effector.  In this repo, Ben add many useful models for birl_baxter which make robot more powerful! Here, I will explain how to add models you want to baxter.

# What is URDF?
The [http://wiki.ros.org/urdf Unified Robot Description Format (URDF)] is the standard ROS XML representation of the robot model (kinematics, dynamics, sensors) describing robots. in addition to URDF, we can also use SDF [http://sdformat.org] which is an XML format that describes objects and environments for robot simulators, visualization, and control. Originally developed as part of the Gazebo robot simulator, SDF was designed with scientific robot applications in mind. For baxter, you can search this wiki [http://sdk.rethinkrobotics.com/wiki/URDF]  Baxter generates his URDF dynamically on robot startup. This model is updated when any gripper is attached or detached, an object is 'grasped' or released and its mass is compensated for, and when new urdf segments are provided/commanded to the gripper plugins. As of SDK versions >= 1.0.0 Baxter's internal robot model, is loaded to the [http://wiki.ros.org/Parameter%20Server parameter server] on the topic <code>/robot_description</code>
The default URDF for Baxter is available in the [https://github.com/RethinkRobotics/baxter_common baxter_common] repository. The package <code> baxter_description </code> contains the URDF and accompanying meshes.

# Model options
## gripper options: 
###    fingers  
     extended_wide 
     extended_narrow 
     standard_narrow
     standard_wide 
     pa_finger
### finger_slot 
        1 2 3 4 5 6
### finger_tip 
    basic_hard_tip
    basic_soft_tip 
    half_round_tip
    paddle_tip none
The model pictures are attached in the media folder.
![extended_narrow](https://github.com/birlrobotics/birl_baxter_common/blob/master/media/extended_narrow.png)
![extended_wide](https://github.com/birlrobotics/birl_baxter_common/blob/master/media/extended_wide.png)
![left_camera_frame](https://github.com/birlrobotics/birl_baxter_common/blob/master/media/left_camera_frame.png)
![no_ft](https://github.com/birlrobotics/birl_baxter_common/blob/master/media/no_ft.png)
![pa_finger](https://github.com/birlrobotics/birl_baxter_common/blob/master/media/pa_finger.png)
![standard_narrow](https://github.com/birlrobotics/birl_baxter_common/blob/master/media/standard_narrow.png)
![standard_wide](https://github.com/birlrobotics/birl_baxter_common/blob/master/media/standard_wide.png)
![SAGA gripper](https://github.com/birlrobotics/birl_baxter_common/blob/master/media/web3.png)
![box](https://github.com/birlrobotics/birl_baxter_common/blob/master/media/box.png)
![gripper_camera_ft](https://github.com/birlrobotics/birl_baxter_common/blob/master/media/gripper_camera_ft.png)

# How to use it?


      <xacro:arg name="gazebo" default="false"/>
      <xacro:arg name="pedestal" default="true"/>
      <xacro:arg name="table" default="false"/>
      <xacro:arg name="asus_xtion" default="false"/>
      <xacro:arg name="right_camera_frame" default="true"/>
      <xacro:arg name="left_camera_frame" default="true"/>
      <xacro:arg name="left_male_holder" default="false"/>  
      <xacro:arg name="right_male_holder" default="false"/>
      <xacro:arg name="l_finger"       default="standard_wide"/>
	  <xacro:arg name="l_finger_slot"  default="1"/>   
	  <xacro:arg name="l_finger_tip"   default="basic_hard_tip"/>
	  <xacro:arg name="l_finger_grasp" default="inner"/>
	  <xacro:arg name="r_finger"       default="standard_wide"/>
	  <xacro:arg name="r_finger_slot"  default="1"/>   
	  <xacro:arg name="r_finger_tip"   default="standard_narrow"/>
	  <xacro:arg name="r_finger_grasp" default="inner"/>
	  <xacro:arg name="left_ft_sensor" default="false"/>
	  <xacro:arg name="right_ft_sensor" default="false"/>
Basically, if you don't want to dig deeper, you can just change the default values. But when you set `right_male_holder` or `left_male_holder` to false, you need comment  the part below otherwise, it won't find joint available.

        <xacro:include filename="$(find birl_baxter_description)/urdf/box/box_male/robots/box_male.URDF" >
        </xacro:include>
      <joint name="right_male_box_joint" type="fixed">
          <origin rpy="0 0 0" xyz="0 0 0.015"/>
          <parent link="right_male_holder" />
          <child link="box_male"/>  
      </joint>
 # Links for learning URDF
 [URDF wiki](http://wiki.ros.org/urdf/Tutorials)  

# TUTORIAL
launch rviz

`roslaunch birl_baxter_description baxter_ft_rviz.launch `

launch gazebo

`roslaunch birl_baxter_description baxter_ft_gazebo.launch`
