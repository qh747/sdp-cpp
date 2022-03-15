file(GLOB SOURCES_LIST CONFIGURE_DEPENDS "${CMAKE_CURRENT_SOURCE_DIR}/*.cpp")

# Make an automatic library - will be static or dynamic based on user setting
add_library(abnf ${SOURCES_LIST})

list(APPEND flags "-fPIC" "-Wall")
if(NOT WIN32)
  list(APPEND flags "-Wextra" "-Wpedantic")
endif()

target_compile_options(abnf
   PRIVATE
   ${flags}
)

# We need this directory, and users of our library will need it too
target_include_directories(abnf
  PUBLIC 
  ../../include
  ../builders
)


