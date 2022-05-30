cmake_minimum_required(VERSION 3.0.2)
set(CMAKE_CUDA_COMPILER /usr/local/cuda/bin/nvcc)
project(bounding_box_msgs)
enable_language(CUDA)
set(CMAKE_CXX_COMPILIER "/usr/bin/g++")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++14 -O3 -Wno-write-strings")
set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} -Wl,-rpath -Wl,$ORIGIN")

find_package(catkin REQUIRED
  COMPONENTS
    message_generation
    sensor_msgs
    std_msgs
    geometry_msgs
)

add_message_files(
  FILES
  boundingbox.msg
  boundingboxes.msg
)


generate_messages(
  DEPENDENCIES
  std_msgs
  geometry_msgs
  sensor_msgs
)

catkin_package(
  CATKIN_DEPENDS
    message_runtime
    sensor_msgs
    std_msgs
    geometry_msgs
)



