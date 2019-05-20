cmake_minimum_required(VERSION 3.5)
project(mara_moveit_tutorials)

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

# add_compile_options(-Wall -Wextra -Wpedantic -Werror=ignored-qualifiers)

find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(rclcpp_action REQUIRED)
find_package(moveit_ros_planning_interface REQUIRED)

include_directories(include)

add_executable(move_group_interface_tutorial
  src/move_group_interface_tutorial.cpp
)
ament_target_dependencies(move_group_interface_tutorial
  rclcpp
  moveit_ros_planning_interface
)

target_include_directories(move_group_interface_tutorial PUBLIC
  ${moveit_ros_planning_interface_INCLUDE_DIRS}
)

target_link_libraries(move_group_interface_tutorial
  ${moveit_ros_planning_interface_LIBRARIES}
)

install(TARGETS
  move_group_interface_tutorial
  DESTINATION lib/${PROJECT_NAME}
)
