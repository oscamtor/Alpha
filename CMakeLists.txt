cmake_minimum_required(VERSION 2.8)
project(Alpha)

#ok
set (MY_MATHLIB_INCLUDE ${CMAKE_CURRENT_SOURCE_DIR}/../Maths)
set (MY_MATHLIB_LIB ${CMAKE_CURRENT_SOURCE_DIR}/../Maths/cmake-build-debug/libmaths.so)
MESSAGE ("OCT -- :MY_MATHLIB_INCLUDE " ${MY_MATHLIB_INCLUDE})
MESSAGE ("OCT -- :MY_MATHLIB_LIB " ${MY_MATHLIB_LIB})
include_directories(${MY_MATHLIB_INCLUDE})
find_library(MY_MATHLIB_LIB maths)

add_executable(alpha main.cpp)

#ko
#target_link_libraries(maths ../Maths/cmake-build-debug/libmaths.so)

#ok
target_link_libraries(alpha ${MY_MATHLIB_LIB})