cmake_minimum_required(VERSION 3.0 FATAL_ERROR)
project (cmakevisualstudio CXX)
add_executable(hello main.cpp)

#set(CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake)
#find_package(Eigen3 REQUIRED)
#include_directories(SYSTEM ${EIGEN3_INCLUDE_DIR}
