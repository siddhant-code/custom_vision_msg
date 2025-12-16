cmake_minimum_required(VERSION 3.0.2)
project(vision_msgs)

find_package(catkin REQUIRED COMPONENTS
  message_generation
  std_msgs
  sensor_msgs
  geometry_msgs)

include_directories(include)

add_message_files(
  DIRECTORY msg
  FILES
  msg/BoundingBox2D.msg
  msg/BoundingBox2DArray.msg
  msg/BoundingBox3D.msg
  msg/BoundingBox3DArray.msg
  msg/Classification.msg
  msg/Detection2DArray.msg
  msg/Detection2D.msg
  msg/Detection3DArray.msg
  msg/Detection3D.msg
  msg/LabelInfo.msg
  msg/ObjectHypothesis.msg
  msg/ObjectHypothesisWithPose.msg
  msg/VisionClass.msg
  msg/Point2D.msg
  msg/Pose2D.msg
  msg/VisionInfo.msg
)

generate_messages(DEPENDENCIES
  std_msgs
  sensor_msgs
  geometry_msgs
)

catkin_package(CATKIN_DEPENDS
  message_runtime
  std_msgs
  sensor_msgs
  geometry_msgs
)

install(DIRECTORY include/${PROJECT_NAME}/
  DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
  FILES_MATCHING PATTERN "*.h"
)

if (CATKIN_ENABLE_TESTING)
  add_subdirectory(test)
endif()
