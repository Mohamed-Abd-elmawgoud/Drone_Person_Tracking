
cmake_minimum_required(VERSION 3.28.3)
project(uav_msgs)

if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 17)
endif()
if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(std_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)


install(
  FILES ros1_bridge_mapping_rules.yaml
  DESTINATION share/${PROJECT_NAME}
)
  
rosidl_generate_interfaces(${PROJECT_NAME}
  "msg/UAVPose.msg"
  DEPENDENCIES std_msgs geometry_msgs
)

ament_package()

