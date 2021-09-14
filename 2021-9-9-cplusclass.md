---
layout: post
title:  "算法过程中用到的C++库"
date:   2021-09-09 13:05
categories: C++库函数
tags:  C++
excerpt: 遇到的C++库
---



# 标准库
vector 可变大小数组，支持快速随机访问，在尾部之外的地方插入或者删除元素很慢
deque 双端队列，支持快速随机访问，头尾插入数据很快
list 双向链表，双向顺序访问，任何位置插入都很快
forward_list 单项链表，单项数据访问
array 固定大小数据，支持快速随机访问
string  与 vector 相似的容器专门用来保存字符，随机访问快，在尾部插入很快。


# 类型篇
pair 将两个数据合并成一个组数据。

map 可以直接通过索引修改 value 

string::substr(pos,n) 从pos下标开始，长度为n的子串。

unordered_set 无序 set 容器


string.push_back();