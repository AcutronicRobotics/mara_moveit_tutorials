cmake_minimum_required(VERSION 2.8.3)
project(mara_moveit_tutorials)

add_compile_options(-std=c++14)

find_package(catkin REQUIRED
  COMPONENTS
    interactive_markers
    moveit_core
    moveit_visual_tools
    moveit_ros_planning
    moveit_ros_planning_interface
    moveit_ros_perception
    pluginlib
    geometric_shapes
    pcl_ros
    pcl_conversions
    rosbag
    tf2_ros
    tf2_eigen
    tf2_geometry_msgs
)

find_package(Eigen3 REQUIRED)
find_package(Boost REQUIRED system filesystem date_time thread)

set(THIS_PACKAGE_INCLUDE_DIRS
  lessons/interactivity/include
)

catkin_package(
  LIBRARIES
    interactivity_utils
  INCLUDE_DIRS
  CATKIN_DEPENDS
    moveit_core
    moveit_visual_tools
    moveit_ros_planning_interface
    interactive_markers
    tf2_geometry_msgs
  DEPENDS
    EIGEN3
)

###########
## Build ##
###########

include_directories(SYSTEM ${THIS_PACKAGE_INCLUDE_DIRS} ${Boost_INCLUDE_DIR} ${EIGEN3_INCLUDE_DIRS})
include_directories(${catkin_INCLUDE_DIRS})
link_directories(${catkin_LIBRARY_DIRS})

add_subdirectory(lessons/robot_model_and_robot_state)
add_subdirectory(lessons/planning_scene)
add_subdirectory(lessons/planning_scene_ros_api)
add_subdirectory(lessons/motion_planning_api)
add_subdirectory(lessons/motion_planning_pipeline)
add_subdirectory(lessons/move_group_interface)
add_subdirectory(lessons/move_group_python_interface)
#add_subdirectory(lessons/collision_environments)
add_subdirectory(lessons/pick_place)
add_subdirectory(lessons/visualizing_collisions)
add_subdirectory(lessons/interactivity)
