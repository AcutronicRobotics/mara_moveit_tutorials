cmake_minimum_required(VERSION 3.10.2)
project(mara_moveit_tutorials)

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

find_package(Eigen3 REQUIRED)

# Eigen 3.2 (Wily) only provides EIGEN3_INCLUDE_DIR, not EIGEN3_INCLUDE_DIRS
if(NOT EIGEN3_INCLUDE_DIRS)
  set(EIGEN3_INCLUDE_DIRS ${EIGEN3_INCLUDE_DIR})
endif()

find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(rclcpp_action REQUIRED)
find_package(moveit_ros_planning_interface REQUIRED)

find_package(Boost REQUIRED system filesystem date_time thread)

###########
## Build ##
###########

include_directories(SYSTEM ${THIS_PACKAGE_INCLUDE_DIRS}
 ${Boost_INCLUDE_DIR}
 ${EIGEN3_INCLUDE_DIRS})

include_directories(${rclcpp_INCLUDE_DIRS}
 ${moveit_ros_planning_interface_INCLUDE_DIRS})

link_directories(${rclcpp_LIBRARY_DIRS})

add_subdirectory(tutorials/move_group_interface)

ament_export_include_directories(include)
ament_export_dependencies(moveit_core)
ament_export_dependencies(moveit_visual_tools)
ament_export_dependencies(moveit_ros_planning_interface)
ament_export_dependencies(EIGEN3)
