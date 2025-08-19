为了让用户可以编写自己的机器人控制程序，ROS提供了两种主流语言C++和Python的编程接口roscpp和rospy，这种接口被称为客户端库（Client Library）（注意！和服务通讯的客户端ServiceClient没有任何关系）。用户的自主开发一般在自创的“工作空间”文件夹中进行。

工作空间（Workspace）是由你自己定义的，用于存放包（Packages）、编译源代码的文件夹，运行`catkin_make`之后，工作空间就成为一个标准的`catkin`空间。在一个定义规范的工作空间中进行开发是良好的习惯。