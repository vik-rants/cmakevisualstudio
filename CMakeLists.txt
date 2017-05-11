cmake_minimum_required(VERSION 2.8 )
project (cmakevisualstudio CXX)

# Add source code and setup folder structure.
set(src ci/main.cpp)

# here we specify the additional include directories for the project.
include_directories(include)

# It specifies the executable name. Here the executable is the first parameter i.e. hello and a file hello.exe will be created.

add_executable(hello ${src})

##Checking all variables
set(CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/cmake)
message("project source dir is : ${PROJECT_SOURCE_DIR}")
message("cmake install prefix is : ${CMAKE_INSTALL_PREFIX}")
message("cmake include path  is : ${CMAKE_INCLUDE_PATH}")
message(STATUS "module path: ${CMAKE_MODULE_PATH} ${CMAKE_ROOT}")
message("Current dir is : ${CMAKE_CURRENT_SOURCE_DIR}/cmake")
#SET(CMAKE_INCLUDE_PATH ${CMAKE_INCLUDE_PATH} "C:/projects/boost")
#SET(CMAKE_LIBRARY_PATH ${CMAKE_LIBRARY_PATH} "C:/win32libs/boost/lib")



#list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake")
find_package(Eigen3 REQUIRED)
include_directories("${EIGEN3_INCLUDE_DIR}")
message("Found Eigen3 in: ${EIGEN3_INCLUDE_DIR}")
