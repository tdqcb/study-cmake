set(LIBHELLO_SRC hello.cpp)
# hello:正常库名，生成的名字前面会加上lib,最终产生的文件是libhello.so
# SHARED:共享库  STATIC:静态库  ${LIBHELLO_SRC}：源文件
add_library(hello_static STATIC ${LIBHELLO_SRC})

#同时构建静态和动态库（静态库的后缀为.a或者.lib  动态库的后缀为.so或者.dll）
#如果用下面这种方式，只会构建一个动态库，不会构建静态库，虽然静态库的后缀是.a
#add_library(hello SHARED ${LIBHELLO_SRC})
#add_library(hello STATIC ${LIBHELLO_SRC})

#修改静态库的名字，但是我们往往希望它们的名字是相同的，只是后缀不同而以
#add_library(hello SHARED ${LIBHELLO_SRC})
#add_library(hello_static STATIC ${LIBHELLO_SRC})

#set_target_properties这条指令可以用来设置输出的名称，对于动态库，还可以用来指定动态库版本和API版本
set_target_properties(hello_static PROPERTIES OUTPUT_NAME "hello")
set_target_properties(hello_static PROPERTIES CLEAN_DIRECT_OUTPUT 1)


add_library(hello SHARED ${LIBHELLO_SRC})
#用于清除
set_target_properties(hello PROPERTIES OUTPUT_NAME "hello")
set_target_properties(hello PROPERTIES CLEAN_DIRECT_OUTPUT 1)

#安装头文件
install(FILES hello.h DESTINATION include/hello)
#安装二进制文件  hello:动态库 LIBRARY DESTINATION：动态库的安装路径   ARCHIVE DESTINATION：静态库的安装路径
install(TARGETS hello hello_static LIBRARY DESTINATION lib ARCHIVE DESTINATION lib)

#安装命令
#cmake -D CMAKE_INSTALL_PREFIX=/usr ..

#使用外部共享库和头文件



