cmake_minimum_required(VERSION 2.8.3)
project(birl_gripper_description)

## Find catkin macros and libraries
find_package(catkin REQUIRED rethink_ee_description)

#############
## Install ##
#############

catkin_package()

foreach(dir meshes urdf)
   install(DIRECTORY ${dir}/
      DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/${dir})
endforeach(dir)
