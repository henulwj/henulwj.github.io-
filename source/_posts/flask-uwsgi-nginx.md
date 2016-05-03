---
title: uwsgi+nginx部署flask应用
date: 2016-04-18 20:53:59
tags:
	- python
	- flask
---

### 写在前面

最近要将做的一个flask的项目部署到服务器上，找了一些方案，最终选定uwsgi+nginx，目前搭建成功了，接下来准备采用supervisor来管理服务进程。

### 1. 基础准备

> 1. Linux服务器
> 2. python
> 3. uwsgi 
> 4. nginx


### 2.