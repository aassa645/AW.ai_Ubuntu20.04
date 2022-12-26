cmake_minimum_required(VERSION 2.8.3)
project(points_downsample)

set(CMAKE_CXX_STANDARD 14)

find_package(catkin REQUIRED COMPONENTS
        roscpp
        geometry_msgs
        sensor_msgs
        pcl_conversions
        pcl_ros
        )



find_package(PCL REQUIRED QUIET)

catkin_package(
        CATKIN_DEPENDS
        roscpp
       
        geometry_msgs
        sensor_msgs
 
        pcl_conversions
        pcl_ros
  
)

include_directories(include ${catkin_INCLUDE_DIRS})

###########
## Build ##
###########

include_directories(include ${catkin_INCLUDE_DIRS})
SET(CMAKE_CXX_FLAGS "-O2 -g -Wall ${CMAKE_CXX_FLAGS}")

add_executable(voxel_grid_filter nodes/points_downsampler.cpp)

add_dependencies(voxel_grid_filter ${catkin_EXPORTED_TARGETS})

target_link_libraries(voxel_grid_filter ${catkin_LIBRARIES})
