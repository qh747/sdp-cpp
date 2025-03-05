add_subdirectory(abnf)
add_subdirectory(builders)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# Make an automatic library - will be static or dynamic based on user setting
add_library(sdp-cpp SessionDescription.cpp)

list(APPEND flags "-fPIC" "-Wall")

if(NOT WIN32)
  list(APPEND flags "-Wextra" "-Wpedantic")
endif()

target_compile_options(sdp-cpp
   PRIVATE
   ${flags}
)

# We need this directory, and users of our library will need it too
target_include_directories(sdp-cpp PUBLIC ${HEADER_PATH})

# This depends on (header only) boost
target_link_libraries(sdp-cpp PRIVATE abnf builders)

