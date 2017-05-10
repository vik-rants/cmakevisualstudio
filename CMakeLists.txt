cmake_minimum_required(VERSION 3.0 )
project (cmakevisualstudio CXX)

# Add source code and setup folder structure.
set(src ci/main.cpp)

# here we specify the additional include directories for the project.
include_directories(include)

# It specifies the executable name. Here the executable is the first parameter i.e. hello and a file hello.exe will be created.

add_executable(hello ${src})

#list( APPEND CMAKE_MODULE_PATH "C:/projects/eigen-eigen-67e894c6cd8f/cmake")
set(CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake)
#find_package(Eigen3 REQUIRED)
#include_directories(SYSTEM ${EIGEN3_INCLUDE_DIR})
#message("Found Eigen3 in: ${EIGEN3_INCLUDE_DIR}")

find_package(Eigen 3 QUIET)
if(NOT Eigen_FOUND)
  include(${PROJ_SOURCE_DIR}/cmake/FindEigen3.cmake)
  set(Eigen_INCLUDE_DIR ${EIGEN3_INCLUDE_DIR})
endif()
include_directories(${Eigen_INCLUDE_DIR})
message("Found Eigen3 in: ${EIGEN3_INCLUDE_DIR}")