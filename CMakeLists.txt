cmake_minimum_required(VERSION 2.8)
project(Alpha)


set (MY_MATHLIB_INCLUDE ${CMAKE_CURRENT_SOURCE_DIR}/../Maths)
set (MY_MATHLIB_LIB ${CMAKE_CURRENT_SOURCE_DIR}/../Maths/cmake-build-debug/libmaths.so)
set (MY_MATHLIB_LIB_DIR ${CMAKE_CURRENT_SOURCE_DIR}/../Maths/cmake-build-debug)
set (MY_MATHLIB_LIB_BASENAME libmaths.so)

MESSAGE ("OCT -- :MY_MATHLIB_INCLUDE " ${MY_MATHLIB_INCLUDE})
MESSAGE ("OCT ok1 -- :MY_MATHLIB_LIB " ${MY_MATHLIB_LIB})
MESSAGE ("OCT ok2-- :MY_MATHLIB_LIB_DIR " ${MY_MATHLIB_LIB_DIR})
MESSAGE ("OCT ok2 -- :MY_MATHLIB_LIB_BASENAME " ${MY_MATHLIB_LIB_BASENAME})

#ok1 (estilo "con find_library" segun https://stackoverflow.com/questions/26222908/cmake-cannot-find-my-library-file)
#include_directories(${MY_MATHLIB_INCLUDE})
#find_library(MY_MATHLIB_LIB maths)

#ok2  (estilo SIN "find_library" como en ipa-native-flujos)
include_directories(${MY_MATHLIB_INCLUDE})

add_executable(${PROJECT_NAME} main.cpp)

#ko
#target_link_libraries(maths ../Maths/cmake-build-debug/libmaths.so)

#ok1  (estilo CON "find_library" y SIN "target_link_directories"   segun https://stackoverflow.com/questions/26222908/cmake-cannot-find-my-library-file)
#target_link_libraries(alpha ${MY_MATHLIB_LIB})


#ok2  (estilo SIN "find_library" y CON "target_link_directories" como en ipa-native-flujos)
target_link_directories(${PROJECT_NAME} PUBLIC ${MY_MATHLIB_LIB_DIR})
target_link_libraries(${PROJECT_NAME} ${MY_MATHLIB_LIB_BASENAME})