#add_executable(hello main.cpp)
#加入头文件搜索路径
include_directories(/usr/local/include/hello)
add_executable(main main.cpp)
#报错找不到HelloFunc()
#添加非标准的共享库搜索路径
#link_directories(/home/myproject/libs)
#添加需要链接的共享库  要求libhello.so在系统变量环境下
TARGET_LINK_LIBRARIES(main /usr/local/lib/libhello.so)
#link_directories(hello /usr/lib/libhello.a)