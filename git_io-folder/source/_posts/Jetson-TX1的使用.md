---
title: Jetson-TX1的使用&ROS_install
date: 2017-08-11 20:24:53
tags: Jetson_Tx1, Jetson_Tx2
toc: true
reward: true
comments: ture
categories: 实习
---
1.刷机与设置教程：
http://blog.csdn.net/jesse_mx/article/details/53315886
JetPack网址：
https://developer.nvidia.com/embedded/jetpack
下载账号：fgq1992@163.com
密码：Fe--------,
2.刷机缓慢，多半网络问题
<!-- more -->
3.software&updates打不开问题， 用sudo apt-get update , sudo apt-get upgrade试一下
4.TX1上安装ROS
```
$ git clone https://github.com/jetsonhacks/installROSTX1.git
$ cd installROSTX1
$ vim installROS.sh
```
将ros-kinetic-ros-base 更改为 ros-kinetic-desktop-full
`./installROS.sh`
Reference
>http://www.ncnynl.com/archives/201705/1634.html
>https://github.com/jetsonhacks/installROSTX1

