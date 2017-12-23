cmake_minimum_required(VERSION 3.9)

project(cpp-netlib)


if (${CMAKE_CURRENT_SOURCE_DIR} STREQUAL ${CMAKE_SOURCE_DIR})
  add_subdirectory(test)
endif()

set( CPP-NETLIB_BUILD_TESTS OFF)
add_subdirectory(cpp-netlib)

add_library(${PROJECT_NAME} cpp-netlib.cpp)
target_include_directories(${PROJECT_NAME} PUBLIC
  cpp-netlib
  cpp-netlib/deps/uri/include
)
target_link_libraries(${PROJECT_NAME} boost_system cppnetlib-server-parsers pthread)
