# 编译安装

在编译使用之前，若为新手或对于编译原理不熟悉的可以参考一下[c++编译流程](cpp_compile)。

---

Client依赖及所需要的工具

* c++17
* CMake(>=3.12.4)
* Qt5(>=5.12)
* zlib(>=1.2.11)
* Protobuf(>=2.6.1)
* Eigen3
* ODE
* OpenGL

Medusa依赖以及所需要的工具：

* c++11
* Qt5(>=5.12)
* Eigen3
* Protobuf(>=2.6.1)
* lua5.1
* tolua++5.1

Ubuntu环境编译SSL文档说明
一、Client
1. 安装Ubuntu18.04
网上有各种超详细的安装教程，有Ubuntu+Windows双系统的，有Ubuntu纯系统的，我建议安装纯系统的。下面给出连接：
https://blog.csdn.net/u014453443/article/details/88049804
https://blog.csdn.net/baidu_36602427/article/details/86548203
2.安装Qt5.14
在网上下载Qt5.14，下载版本为qt-opensource_linux-x64-5.14.0.run，双击运行run文件，并安装到~/目录下。
Qt下载路径：http://download.qt.io/archive/qt/5.14/5.14.0/

接下来是各种编译所需依赖包的安装
3.zlib安装
Zlib是一个压缩函数库，安装比较简单，在termial下直接敲命令安装（termial打开方式crtl_alt+t）。
Zlib安装教程： https://blog.51cto.com/xxaqustc/1166371
安装教程我一般提供1-2个，都是我亲测过了，你们可以相互借鉴参考。同下
4.Eigen3安装
Eigen3是一个矩阵运算函数库
Eigen安装教程： https://blog.csdn.net/xiat5/article/details/79162617
https://www.cnblogs.com/newneul/p/8256803.html
注意：apt-get安装的包，一般都是在/usr/local/include/下的，如果目录下有eigen，说明安装成功。同下
5.Protobuf的安装
Protobuf是google公司推出的一种数据传输格式，需要安装此协议格式的解析函数包。
安装教程：https://blog.csdn.net/kdchxue/article/details/81046192
https://blog.csdn.net/triplestudio/article/details/93591161
用git clone下载protobuf会很慢，建议直接在goole protobuf源地址下载（https://github.com/protocolbuffers/protobuf）
6、OpenGL 安装
openGL是一个开源的图形函数库，安装教程：https://blog.csdn.net/huangkangying/article/details/82022177
https://blog.csdn.net/renhaofan/article/details/82631082
7、Cmake安装
Cmake3.16在ubuntu1804下有问题，建议装cmake3.14。
安装教程：https://blog.csdn.net/stanfan/article/details/88681165
教程中的案例是ubuntu1604，但是和1804方法是一样的。
8.ODE安装
ODE是一个开源的动态引擎库，给client仿真提供支持。
Ode的安装教程： https://www.dazhuanlan.com/2019/12/17/5df7b25f579d0/
最后，需要在GitHub上下载ChinaOpenSSL的开源代码，地址是https://github.com/Robocup-ssl-China/ChinaOpenSSL，建议注册github后下载。
安装好ubuntu系统，下载好小型足球机器人SSL开源代码，安装好IDE工具和各种依赖包，现在就可以开始编译开源代码了。
运行QtCreator，可以在主桌面右下角显示应用程序中搜索，也可以在Qt5.14->Tools->QtCreator->bin目录下打开qtcreator。
在QtCreator工具栏文件->打开文件或项目中，打开下载的ChinaOpenSSL开源代码包Client文件夹下的CMakeLists.txt文件。Client项目代码添加到QtCteator中。单击QtCreator工具栏中构建按钮，选择“执行CMake”，IDE开始根据调用gcc/c++17编译器解析CMakeLists.txt编译整个项目。
如果一切顺利，编译输出会提示编译成功，并告诉你编译结果放在那里了。在命令行终端（Ctrl+Shift+T）进入ZBin目录，输入./Client执行，就可以看到client界面了。
二、Medusa

Client是小型足球机器人的控制终端，Medusa是真正的后台程序。编译Medusa需要lua5.1和to lua++这两个依赖库。
Lua5.1安装教程：https://mobile.51cto.com/iphone-288738.htm
Tolua++安装教程：https://www.dazhuanlan.com/2019/10/05/5d97c3a14c67f/
然后打开QtCreator，在QtCreator工具栏文件->打开文件或项目中，打开下载的ChinaOpenSSL开源代码包Medusa中的Medusa.pro文件。在项目栏中选择medusa，单击右键，选择qmake，开始执行编译。这是，编译会报错，提示“Norule to make target”share/proto/cpp/grSim_Commands.pb.cc”。
在下载的ChinaOpenSSL文件夹下找到auto_linux.sh脚本。执行它，会生成我们需要的grSim_Commands.pb.cc和lua_zeus.cpp，然后把gSim_Commads.pb.cc拷贝到Qt报错提示的目录下，再次执行qmake。如果还是报错，关闭Medusa，然后在重新加载，执行编译，就应该OK了。






