#让hello world 看起来向一个工程
# 1 为工程添加一个子目录src ,用来放置工程源代码
# 2 添加一个子目录doc ,用来放置这个工程的文档hello.txt
# 3 在工程目录添加文本文件copyright,readme
# 4 在工程目录添加一个runhello.sh脚本，用来调用hello二进制
# 5 将构建后的目标文件放入构建目录的bin子目录
# 6 将doc目录的内容以及copyright/readme 安装到/usr/share/doc/cmake/
project(Hello)
# add_subdirectory(source_dir [binary_dir])  用于向当前工程添加存放源文件的子目录，并可以指定中间二进制和目标二进制存放的位置
# add_subdirectory(src bin)  将src子目录加入工程并指定编译输出（包含编译中间结果）路径为bin目录
add_subdirectory(src bin)
#安装
# 1. 一种是从代码编译后直接make install安装
# 2. 一种是打包时指定目录安装    简单的可以这样指定目录： make install DESTDIR=/tmp/test  稍微复杂一点可以这样指定目录：./configure -prefix=/usr

install(FILES COPYRIGHT README DESTINATION /usr/local/share/doc/cmake/)
install(PROGRAMS runhello.sh DESTINATION bin)
install(DIRECTORY doc/ DESTINATION share/doc/cmake)

#安装脚本 runhello.sh  PROGRAMS:非目标文件的可执行程序安装（比如脚本之类的）
#INSTALL(PROGRAMS runhell.sh DESTINATION bin)  使用了相对路径，实际安装到的是/usr/bin
#DIRECTORY   后面连接的是所在Source目录的相对路径
#doc/:  目录名不加/ 将这个目录安装到目标路径  目录加/：将这个目录中的内容安装到目标路径

#静态库和动态库的构建
#静态库的扩展名一般为.a或.lib;动态库的扩展名一般为.so 或.dll
#静态库在编译时会直接整合到目标程序中，编译成功的可执行文件可独立运行
#动态库在编译时不会放到连接的目标程序中，即可执行文件无法单独运行

