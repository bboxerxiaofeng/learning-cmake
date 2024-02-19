cmake_minimum_required(VERSION 2.8.4)

set(LIBHELLO_SRC hello.c)

add_library(hello_dynamic SHARED ${LIBHELLO_SRC})  # SHARED表示hello_dynamic是动态库 
add_library(hello_static STATIC ${LIBHELLO_SRC})   # STATIC表示hello_static是动态库 

set_target_properties(hello_dynamic PROPERTIES OUTPUT_NAME "hello")      # 动态库的名字设置为hello
set_target_properties(hello_dynamic PROPERTIES VERSION 1.2 SOVERSION 1)  # VERSION指代动态库版本，SOVERSION指代API版本

set_target_properties(hello_static PROPERTIES OUTPUT_NAME "hello")       # 静态库的名字设置为hello

set(LIBRARY_OUTPUT_PATH ${PROJECT_BINARY_DIR}/lib) # 设置共享库的输出路径是lib目录

install(TARGETS hello_dynamic hello_static         # DESTINATION 指定安装到目录lib 安装的具体全路径是通过cmake -DCMAKE_INSTALL_PREFIX=/usr ..来指定,如果没有指定,那么就默认是/usr/local
        LIBRARY DESTINATION lib
        ARCHIVE DESTINATION lib)
        
install(FILES hello.h DESTINATION include/hello)   # DESTINATION 指定安装到目录include/hello
