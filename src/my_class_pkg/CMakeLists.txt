cmake_minimum_required(VERSION 3.0.2) 
project(my_class_pkg)

find_package(catkin REQUIRED 
	COMPONENTS roscpp rospy std_msgs
	message_generation
	actionlib
	actionlib_msgs
	sensor_msgs
  	geometry_msgs
)


add_message_files(
	DIRECTORY msg
	FILES MyMessage.msg
)

add_service_files(
	DIRECTORY srv
	FILES MyServiceMsg.srv
)

add_action_files(
	DIRECTORY action
	FILES MyAction.action
)


generate_messages(
DEPENDENCIES std_msgs 
DEPENDENCIES actionlib_msgs
)

catkin_package(
	CATKIN_DEPENDS 
	message_runtime
	actionlib 
	actionlib_msgs
)

include_directories(include ${catkin_INCLUDE_DIRS})

add_executable(ros_publisher_node src/ros_publisher.cpp) 
target_link_libraries(ros_publisher_node ${catkin_LIBRARIES})
add_executable(ros_subscriber_node src/ros_subscriber.cpp) 
target_link_libraries(ros_subscriber_node ${catkin_LIBRARIES})
add_executable(msg_publisher_node src/msg_publisher.cpp)
target_link_libraries(msg_publisher_node ${catkin_LIBRARIES})
add_executable(msg_subscriber_node src/msg_subscriber.cpp)
target_link_libraries(msg_subscriber_node ${catkin_LIBRARIES})
add_executable(ros_server_node src/ros_server.cpp) 
target_link_libraries(ros_server_node ${catkin_LIBRARIES})
add_executable(ros_client_node src/ros_client.cpp) 
target_link_libraries(ros_client_node ${catkin_LIBRARIES})
add_dependencies(ros_client_node ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
add_executable(ros_action_server src/ros_action_server.cpp) 
target_link_libraries(ros_action_server ${catkin_LIBRARIES})
add_executable(ros_action_client src/ros_action_client.cpp) 
target_link_libraries(ros_action_client ${catkin_LIBRARIES})
add_executable(ros_bump_node src/ros_bump.cpp) 
target_link_libraries(ros_bump_node ${catkin_LIBRARIES})
add_executable(ros_bumpavoid_node src/ros_bumpavoid.cpp)
target_link_libraries(ros_bumpavoid_node ${catkin_LIBRARIES})

