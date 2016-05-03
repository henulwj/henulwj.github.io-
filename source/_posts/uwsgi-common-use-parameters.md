---
title: uwsgi-common-use-parameters
date: 2016-04-20 09:37:52
tags:
	- uwsgi
---

#### 一、uWSGI简介

uWSGI是一个Web服务器，它实现了WSGI协议、uwsgi、http等协议。Nginx中HttpUwsgiModule的作用是与uWSGI服务器进行交换。

WSGI / uwsgi / uWSGI 区分。

- WSGI是一种通信协议。
- uwsgi同WSGI一样是一种通信协议。
- 而uWSGI是实现了uwsgi和WSGI两种协议的Web服务器。

uwsgi协议是一个uWSGI服务器自有的协议，据说该协议大约是fcgi协议的10倍那么快。它用于定义传输信息的类型（type of information），每一个uwsgi packet前4byte为传输信息类型描述，它与WSGI相比是两样东西。

有同学问为什么有了uWSGI还需要nginx




#### 参考

1. [uWSGI配置文档翻译](http://www.cnblogs.com/zhouej/archive/2012/03/25/2379646.html)