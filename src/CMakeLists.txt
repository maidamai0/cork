file(GLOB items *)
foreach(item ${items})
    if(IS_DIRECTORY ${item})
        message(STATUS "include dir: ${item}")
        include_directories(${item})
    endif()
endforeach()

file(GLOB_RECURSE srcs *.cpp *.c)
list(REMOVE_ITEM srcs ${CMAKE_CURRENT_LIST_DIR}/off2obj.cpp)
add_executable(cork ${srcs})

add_executable(off2obj ${CMAKE_CURRENT_LIST_DIR}/off2obj.cpp)