---
title: 创建博客create github.io
date: 2017-08-15 16:50:25
tags: creat_blog
toc: true
reward: true
comments: ture
categories: 实习
---
1.安装Nodejs
```
sudo apt-get install nodejs
sudo apt-get install nodejs-legacy 
sudo apt-get install npm
```
2.安装Hexo
```
npm install hexo-cli -g
```
3.初次使用
<!-- more -->
```
cd ~
mkdir fenggit #初始化博客 
hexo init tusimple
npm install #node.js的命令，根据博客既定的dependencies配置安装所有的依赖包
```
4.配置博客
配置_config.yml,参考http://www.jianshu.com/p/e99ed60390a8
5.创建一篇文章
先把发布到网上的工具下下来
```
npm install hexo-deployer-git --save
```
然后
```
cd tusimple/
hexo new "creat github.io"
hexo g
hexo s #本地发布
hexo d #发布到网上
```
Reference:
http://www.jianshu.com/p/e99ed60390a8
https://masterizumi.github.io/

6.Hexo 主题设置
```
.cd ~/feng_git/tusimple/themes/
.git clone (theme address)
```
配置 _config.yml,然后执行`git pull` 
```
cd ~/feng_git/tusimple
hexo g
hexo s
```
7.发布到网页上Deploy the webpage on GitHub:
`cd ~/feng_git/tusimple/`执行以下命令：
npm install hexo-deployer-get --save #安装deployer,之后不需要
```
hexo clean
hexo g
hexo d
```
8.设置所有文章的目录（已成功）
加载 hexo-generator-json-content: `npm i -S hexo-generator-json-content`  如果报错，可能是nodejs版本太低，需要升级。
arm-ubuntu升级nodejs不能使用网上常用的方法，即 `npm install -g n; n stable`，可以直接去官网 (https://nodejs.org/en/download/) 下载对应的ARM版本的node.js，然后配置全局变量即可
```
sudo mv node-v6.11.3-linux-arm64 /usr/local/
sudo gedit /etc/profile
```
在文件末尾输入：
```
export NODE_HOME=/usr/local/node-v6.11.3-linux-arm64
export PATH=$NODE_HOME/bin:$PATH
```
然后执行`source /etc/profile`生效。
为了避免每次开终端都需要source一下，可以在.bashrc里直接写入`source /etc/profile`
**原来不成功的原因：手长把mathjax设置成了ture,该网页模板有个bug,就是mathjax: true的时候smart_menu不显示内容**

Reference:
http://www.jianshu.com/p/1fb65c61fa4a

