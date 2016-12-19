cmake_minimum_required(VERSION 2.8.3)
project(birl_baxter_description)

find_package(catkin REQUIRED baxter_gazebo)

catkin_package()

foreach(dir meshes urdf  config launch launch/demo launch/pa_box launch/pa_snap launch/sake_gripper )
   install(DIRECTORY ${dir}/
      DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/${dir})
endforeach(dir)
