cmake_minimum_required(VERSION 3.10)
project(cmake_zlib)

set(CMAKE_C_STANDARD 99)

SET(zlib_LIBRARY_SOURCES compress.c crc32.c adler32.c deflate.c gzclose.c gzlib.c gzread.c gzwrite.c infback.c inffast.c inflate.c inftrees.c trees.c uncompr.c zutil.c)
SET(zlib_LIBRARY_HEADERS crc32.h deflate.h gzguts.h inffast.h inffixed.h inflate.h inftrees.h trees.h zconf.h zlib.h zutil.h)

if (MSVC)
    set(CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS TRUE)
endif()

set(LIBRARY_OUTPUT_PATH ${CMAKE_SOURCE_DIR}/lib)

#set(CMAKE_LIBRARY_OUTPUT_DIRECTORY lib)
#set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY lib)

add_library(zlib SHARED ${zlib_LIBRARY_SOURCES} ${zlib_LIBRARY_HEADERS})
add_library(zlib_st STATIC ${zlib_LIBRARY_SOURCES} ${zlib_LIBRARY_HEADERS})
SET_TARGET_PROPERTIES(zlib_st PROPERTIES OUTPUT_NAME zlib)

target_include_directories(zlib INTERFACE ${CMAKE_CURRENT_SOURCE_DIR})
set(LIBRARY_OUTPUT_PATH ${CMAKE_SOURCE_DIR}/lib)