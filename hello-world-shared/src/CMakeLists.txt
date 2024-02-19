cmake_minimum_required(VERSION 2.8.4)

add_executable(main main.c)

include_directories(../include/hello)                       # 指定头文件的搜索路径

find_library(HELLO_LIB NAMES hello PATHS "../lib/")         # 指定动态库的搜索路径

message(STATUS "Library path HELLO_LIB is " ${HELLO_LIB})

target_link_libraries(main ${HELLO_LIB})

set(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin)
