cmake_minimum_required(VERSION 3.24)
project(cork)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_EXTENSIONS OFF)

if(WIN32)
    add_compile_definitions(_USE_MATH_DEFINES NOMINMAX NO_TIMER)
endif()

add_compile_definitions(ANSI_DECLARATORS REDUCED CDT_ONLY TRILIBRARY)

find_library(mpir_lib NAMES mpir REQUIRED)
find_file(mpir_inc NAMES mpir.h REQUIRED)
message(STATUS "mpir_lib is ${mpir_lib}")
message(STATUS "mpir_inc is ${mpir_inc}")

include_directories(${mpir_inc}/../)
link_libraries(${mpir_lib})

add_subdirectory(src)