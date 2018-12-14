cmake_minimum_required(VERSION 2.8)

project (mit-hrtf-lib)
set(CMAKE_BUILD_TYPE Release)

include_directories(${PROJECT_SOURCE_DIR}/include)
include_directories(${PROJECT_SOURCE_DIR}/source)
include_directories(${PROJECT_SOURCE_DIR}/source/normal)

add_library(libmit_hrtf_lib STATIC ${PROJECT_SOURCE_DIR}/source/mit_hrtf_lib.c)
