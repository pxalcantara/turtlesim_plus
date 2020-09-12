cmake_minimum_required(VERSION 3.0.2)
project(turtlesim_plus)

find_package(catkin REQUIRED COMPONENTS geometry_msgs message_generation rosconsole roscpp roscpp_serialization roslib rostime std_msgs std_srvs)

find_package(Qt5Widgets REQUIRED)
find_package(Boost REQUIRED COMPONENTS thread)

include_directories(include ${catkin_INCLUDE_DIRS} ${Boost_INCLUDE_DIRS})
link_directories(${catkin_LIBRARY_DIRS})

add_message_files(DIRECTORY msg FILES
                  Color.msg Pose.msg)
add_service_files(DIRECTORY srv FILES
                  Kill.srv
                  SetPen.srv
                  Spawn.srv
                  TeleportAbsolute.srv
                  TeleportRelative.srv)
generate_messages(DEPENDENCIES geometry_msgs std_msgs std_srvs)

catkin_package(CATKIN_DEPENDS geometry_msgs message_runtime std_msgs std_srvs)

set(turtlesim_node_SRCS
  src/turtlesim.cpp
  src/turtle.cpp
  src/turtle_frame.cpp
)
set(turtlesim_node_HDRS
  include/turtlesim/turtle_frame.h
)

qt5_wrap_cpp(turtlesim_node_MOCS ${turtlesim_node_HDRS})


add_executable(turtlesim_node1 ${turtlesim_node_SRCS} ${turtlesim_node_MOCS})
target_link_libraries(turtlesim_node1 Qt5::Widgets ${catkin_LIBRARIES} ${Boost_LIBRARIES})
# add_dependencies(turtlesim_node1 turtlesim_gencpp)

add_executable(turtle_teleop_key1 tutorials/teleop_turtle_key.cpp)
target_link_libraries(turtle_teleop_key1 ${catkin_LIBRARIES})
# add_dependencies(turtle_teleop_key1 turtlesim_gencpp)
add_executable(draw_square1 tutorials/draw_square.cpp)
target_link_libraries(draw_square1 ${catkin_LIBRARIES} ${Boost_LIBRARIES})
# add_dependencies(draw_square1 turtlesim_gencpp)
add_executable(mimic1 tutorials/mimic.cpp)
target_link_libraries(mimic1 ${catkin_LIBRARIES})
# add_dependencies(mimic1 turtlesim_gencpp)/

install(TARGETS turtlesim_node1 turtle_teleop_key1 draw_square1 mimic1
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})

install(DIRECTORY images
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
  FILES_MATCHING PATTERN "*.png" PATTERN "*.svg")
