---
title: tx2 提速
date: 2017-09-19 17:12:14
tags: Jetson_Tx1, Jetson_Tx2
comments: ture
categories: 实习
toc: true
reward: true
---
### 1.使用Nvpmodel
NVIDIA的命令工具Nvpmodel, 提供了5中不同的运行状态:
![nvpmodel_mode](img/nvpmodel_mode.png)
命令如下：
<!-- more -->
```
sudo nvpmodel -m 0  #最高模式MAXN,6个cpu全部开启
sudo nvpmodel --q --verbose  #常看当前模式，cpu数
sudo ./tegrastats  #查看cpu、gpu占的比例
```
### 2.提高时钟
`sudo ./jetson_clock.sh  #提高功耗到15W`
### 3.提高进程优先级
`renice -n -20 -p pid  #提高优先级`
