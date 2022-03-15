# Works with 3.11 and tested through 3.21
cmake_minimum_required(VERSION 3.11...3.21)

# Project name and a few useful settings. Other commands can pick up the results
project(SdpCpp
  VERSION 0.1
  DESCRIPTION "An sdp parser used cpp"
  LANGUAGES CXX)

# Only do these if this is the main project, and not if it is included through add_subdirectory
if(CMAKE_PROJECT_NAME STREQUAL PROJECT_NAME)

  # Optionally set things like CMAKE_CXX_STANDARD, CMAKE_POSITION_INDEPENDENT_CODE here
  set(CMAKE_CXX_STANDARD 11)
  set(CMAKE_CXX_STANDARD_REQUIRED ON)
  set(CMAKE_POSITION_INDEPENDENT_CODE True)
  # Let's ensure -std=c++xx instead of -std=g++xx
  set(CMAKE_CXX_EXTENSIONS OFF)

endif()

# The compiled library code is here
add_subdirectory(src)

