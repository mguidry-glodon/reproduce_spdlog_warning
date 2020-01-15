cmake_minimum_required(VERSION 3.15)
project(reproduce_spdlog_warning)

set(CMAKE_CXX_STANDARD 17)

include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup()

add_library(my_header INTERFACE)
target_include_directories(my_header INTERFACE include)
target_sources(my_header INTERFACE source/my_header.cpp)

add_executable(main)
target_include_directories(main PRIVATE include)
target_sources(main PRIVATE main.cpp)
target_link_libraries(main PRIVATE my_header ${CONAN_LIBS})
