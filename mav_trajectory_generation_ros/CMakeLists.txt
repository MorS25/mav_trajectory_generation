cmake_minimum_required(VERSION 2.8.3)
project(mav_trajectory_generation_ros)

find_package(catkin_simple REQUIRED)
catkin_simple(ALL_DEPS_REQUIRED)

set(CMAKE_MACOSX_RPATH 0)
add_definitions(-std=c++11)

#############
# LIBRARIES #
#############
cs_add_library(${PROJECT_NAME}
  src/trajectory_sampling.cpp
  src/ros_conversions.cpp
  src/ros_visualization.cpp
)

############
# BINARIES #
############
cs_add_executable(trajectory_sampler_node
  src/trajectory_sampler_node.cpp
)
target_link_libraries(trajectory_sampler_node ${PROJECT_NAME})

##########
# EXPORT #
##########
cs_install()
cs_export()
