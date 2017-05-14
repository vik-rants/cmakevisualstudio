cmake_minimum_required(VERSION 2.8 )
project (cmakevisualstudio CXX)

# Add source code and setup folder structure.
set(src ci/main.cpp)

# here we specify the additional include directories for the project.
include_directories(include)

# It specifies the executable name. Here the executable is the first parameter i.e. hello and a file hello.exe will be created.

add_executable(hello ${src})

###Search for packages and External Libraries###
#Set the module path
set(CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/cmake)

# Find package : Eigen3 calling Findeigen.cmake
find_package(Eigen3 REQUIRED)
include_directories("${EIGEN3_INCLUDE_DIR}")
message("Found Eigen3 in: ${EIGEN3_INCLUDE_DIR}")

# Find package : Boost preinstalled
find_package(Boost COMPONENTS filesystem system program_options REQUIRED)
include_directories(${Boost_INCLUDE_DIRS})
list(APPEND LIBRARIES ${Boost_LIBRARIES})

# Find package : Sqlite3 calling Find.cmake

#find_package(Sqlite3 REQUIRED)
#include_directories(${SQLITE3_INCLUDE_DIR})
#list(APPEND LIBRARIES ${SQLITE3_LIBRARY})

# Find package : OpenMP
find_package(OpenMP REQUIRED)
if (OPENMP_FOUND)
set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${OpenMP_CXX_FLAGS}")

# Find GSL
find_package(GSL REQUIRED)
include_directories(${GSL_INCLUDE_DIRS})
list(APPEND LIBRARIES ${GSL_LIBRARIES})


# get version info from git
find_package(Git REQUIRED)
execute_process(
  COMMAND "${GIT_EXECUTABLE}" describe --tags --always
  WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}"
  OUTPUT_VARIABLE VERSION
  OUTPUT_STRIP_TRAILING_WHITESPACE )
string(REGEX REPLACE "v(.+)" "\\1" VERSION_WITHOUT_LEADING_V ${VERSION})

#Python
find_package(PyUIC REQUIRED)
find_package(PythonInterp 3 REQUIRED)