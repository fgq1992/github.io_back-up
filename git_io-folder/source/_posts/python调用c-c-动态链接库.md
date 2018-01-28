---
title: python调用c/c++动态链接库
date: 2017-08-17 17:12:27
tags: python, c++, gcc
comments: ture
categories: 实习
toc: true
reward: true
---

1.C++源码: quick_sort()
<!-- more -->
```
#include <iostream>
#include <stdio.h>
using namespace std;
class TestLib
{
	public:
		
		int quick_sort(int *a, int low, int high);
		void msgshow(char msg[]);
		int example();
		float add(float x, float y);
};
int TestLib:: quick_sort(int *a,int low,int high)
{
	
	if(low>=high)
		return 0;
	int key=a[low];
	int left=low,right=high;
	while(left<right)
	{
		while(a[right]>key&&left<right)
		 	right--;
		a[left++]=a[right];
		while(a[left]<key&&left<right)
			left++;
		a[right--]=a[left];
	}
	a[left]=key;
	quick_sort(a,low,left-1);
	quick_sort(a,right+1,high);
}
void TestLib:: msgshow(char msg[])
{
	printf("enter msgshow succeed\n");
	printf("%s\n",msg);
	return;
}

int TestLib::example()
{
	int a[]={7,7,7,8,8,8,8,8,8,8,9,9,9,0,0,0,0,0,0,0};
	quick_sort(a,0,sizeof(a)/sizeof(a[1])-1);
	char b;
	cout<<sizeof(b)<<endl;
	for(int i=0; i<sizeof(a)/sizeof(a[1]);i++)
	{
		cout<<a[i]<<" ";
	}
	cout<<endl;
	char msg[]="msg test in example";
	msgshow(msg);
	return 0;	
}
float TestLib::add(float x,float y)
{
	return x+y;
}

extern "C"
{
	TestLib obj;
	void msgshow(char msg[])
	{
		obj.msgshow(msg);	
	};
	int example()
	{
		return obj.example();
	}	
	int quick_sort(int *a, int low, int high)
	{
		return obj.quick_sort(a,low,high);
	}
	float add(float x, float y)
	{
		return obj.add(x,y);
	}
}
```
2.编译
```
gcc -c main main.c  #只编译，生成.o文件
gcc -o app main.c   #生成可执行文件
gcc -shared main.c -o main.so  #生成动态链接库 
```
3.python 调用源程序
```
#!usr/bin/python3
#-*- coding:utf-8 -*-

from ctypes import *
import os

#print(os.getcwd()+'quick_sort.so')
test=cdll.LoadLibrary(os.getcwd()+'/quick_sort.so')


#ctypes 使用指针
data2=c_int(10)
pdata2=pointer(data2)  #p(x)创建并返回一个指向 x 的指针实例
print 'pdata2',pdata2
print data2.value
data2.value=4
print data2.value        
null_ptr = POINTER(c_int)() #不带参数的调用指针类型创建一个NULL指针， NULL指针有一个False布尔值
print bool(null_ptr) #POINTER(type) 返回一个类型，这个类型是指向 type 类型的指针类型， type 是 ctypes 的一个类型

#ctypes 使用数组变量
Array=c_int * 5
data1=Array(10,4,7,3,6)
print 'data1',pointer(data1)  
for i in data1:print i

#ctypes 使用string
data3=create_string_buffer(10)
print data3.raw
data3.value='student'
print data3.raw,repr(data3.raw)
data3.value='bag'
print data3.raw
print data3.value

#ctypes 调用C++
#test.example()
test.msgshow('hello msgshow')
#test.quick_sort.restype=c_int
#test.quick_sort.argtypes=(c_void_p,c_int,c_int)
data4=(c_int *8) (0,5,7,3,2,5,6,7)
print test.quick_sort(data4,0,7)
for i in data4: print i
test.add.restype=c_float
test.add.argtypes=(c_float,c_float)
print test.add(1.2,2.4)
```
Reference:
>http://www.cnblogs.com/night-ride-depart/p/4907613.html
>http://blog.csdn.net/taiyang1987912/article/details/44779719
>http://blog.csdn.net/linda1000/article/details/12623527





