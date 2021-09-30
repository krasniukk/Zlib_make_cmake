cmake_minimum_required(VERSION 3.10)
project(cmake_zlib)

set(CMAKE_C_STANDARD 99)

add_subdirectory(../library bin)

add_executable(example example.c)
target_link_libraries(example zlib)

add_executable(minigzip example.c)
target_link_libraries(minigzip zlib)

