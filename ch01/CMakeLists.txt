project(HELLO CXX)   #指定工程的名字和支持的语言，默认支持所有语言
set(src_list helloword.cpp)   #用来显示指定的变量，如果helloword.cpp有空格就必须加双引号
#message:向终端输出用户自定义的信息 主要包含三种信息： 1 SEND_ERROR 产生错误，生成过程被跳过
# 2 STATUS:输入前缀为--的信息   3 FATAL_ERROR:立即终止所有cmake过程
message(STATUS "this is Binary dir "${HELLO_BINARY_DIR})   #向终端输出用户自定义的信息 主要有3
message(STATUS "this is source dir" ${HELLO_SOURCE_DIR})
#  add_executable 生成可执行文件
add_executable(helloword ${src_list})
# 指令与大小写无关，推荐大写


#cmake 内部构建和外部构建
#内部构建：直接在有CMakeLists.txt文件中cmake . （ .表示当期目录）这样会产生的临时文件多，不方便清理
#外部构建： 在build目录下cmake .. (..表示上一级目录)