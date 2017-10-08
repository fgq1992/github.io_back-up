---
title: install_Hokuyo_URG-04lx
date: 2017-08-11 19:50:05
tags: hokuyo
comments: ture
categories: 实习
toc: true
reward: true
---
1.安装hokuyo-URG-04lx：
```
$ cd ~/catkin-ws/src/
$ git clone https://github.com/ros-drivers/urg_c.git
$ cd ..
$ catkin_make
```
2.安装中遇到的问题及解决方案：
<!-- more -->
- missing pcl in /usr/include/: 
```
$ sudo apt-get install tcl8.6
$ cd /usr/include/
$ mv tcl8.6/ tcl
```
- missing laser_proc
```
$ sudo apt-get install ros-kinetic-laser-proc 
```
3.或者直接用最简单的安装方法：
```
$ sudo apt-get install ros-kinetic-urg-node
```
4.安装完后
```
$ ls -l /dev/ttyACM0
$ sudo chmod a+rw /dev/ttyACM0  #可读写
```


