cmake_minimum_required(VERSION 3.0 )
project (cmakevisualstudio CXX)

# Add source code and setup folder structure.
set(src ci/main.cpp)

# here we specify the additional include directories for the project.
include_directories(include)

# It specifies the executable name. Here the executable is the first parameter i.e. hello and a file hello.exe will be created.

add_executable(hello ${src})

#set(CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake)
#find_package(Eigen3 REQUIRED)
#include_directories(SYSTEM ${EIGEN3_INCLUDE_DIR})
