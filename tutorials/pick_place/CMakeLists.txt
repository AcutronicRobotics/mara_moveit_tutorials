add_executable(pick_place src/pick_place_tutorial.cpp)
target_link_libraries(pick_place ${rclcpp_LIBRARIES} ${Boost_LIBRARIES} ${moveit_ros_planning_interface_LIBRARIES})
install(TARGETS pick_place DESTINATION lib/${PROJECT_NAME})
