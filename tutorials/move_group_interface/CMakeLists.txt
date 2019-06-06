add_executable(move_group_interface src/move_group_interface_tutorial.cpp)
target_link_libraries(move_group_interface ${rclcpp_LIBRARIES} ${Boost_LIBRARIES} ${moveit_ros_planning_interface_LIBRARIES})
install(TARGETS move_group_interface DESTINATION lib/${PROJECT_NAME})
