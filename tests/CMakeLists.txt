cmake_minimum_required(VERSION 3.10)
project(Parser)

# 设置C++标准
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED True)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# 指定可执行程序的源文件
set(SOURCES parser.cpp)

# 创建可执行程序
add_executable(${PROJECT_NAME} ${SOURCES})

add_dependencies(${PROJECT_NAME} sdp-cpp abnf builders)

# 添加依赖库路径
target_link_directories(${PROJECT_NAME} PRIVATE ${LIBRARY_PATH})

# 添加头文件路径
target_include_directories(${PROJECT_NAME} PRIVATE ${HEADER_PATH})

# 链接静态库
target_link_libraries(${PROJECT_NAME} PRIVATE sdp-cpp)
target_link_libraries(${PROJECT_NAME} PRIVATE abnf)
target_link_libraries(${PROJECT_NAME} PRIVATE builders)

