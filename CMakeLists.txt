cmake_minimum_required(VERSION 3.1)

add_subdirectory(clew)

project(enumDevices)

set(CMAKE_CXX_STANDARD 11)

add_executable(${PROJECT_NAME} main.cpp)
target_link_libraries(${PROJECT_NAME} libclew)
