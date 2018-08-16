cmake_minimum_required(VERSION 3.1)

project(enumDevices)

set(CMAKE_CXX_STANDARD 11)

find_package(OpenCL REQUIRED)

include_directories(${OPENCL_INCLUDE_DIR})

add_executable(${PROJECT_NAME} main.cpp)
target_link_libraries(${PROJECT_NAME} ${OpenCL_LIBRARY})
