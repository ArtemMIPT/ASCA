cmake_minimum_required(VERSION 3.3)
project(mf)

set(CMAKE_C_FLAGS  "${CMAKE_C_FLAGS} -std=c99 -Ofast -DNDEBUG")

list (APPEND SOURCES chunkmanager.c hash_table.c lists.c logger.c mapped_file.c)

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/out)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/out)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/out)

add_library(mappedfile STATIC ${SOURCES})
add_executable(tester test/test.c)
target_link_libraries(tester mappedfile)
