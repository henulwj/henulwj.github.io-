---
title: Python字符串拼接
date: 2016-01-17 10:54:59
tags: 
  - joint
categories: 
  - python
---
### **Python字符串拼接**
在Python的实际开发中，很多都需要用到字符串拼接，Python中字符串拼接有很多，今天总结一下：

- 用`+`符号拼接
- 用`%`符号拼接
- 用`join()`方法拼接
- 用`format()`方法拼接
- 用`string`模块中的`Template`对象


<!-- more -->

如果还有其他方法，欢迎补充。
例子：

``` python
	fruit1 = 'apples'
	fruit2 = 'bananas'
	fruit3 = 'pears'
```
要求：
输出字符串'There are apples, bananas, pears on the table'

#### **1. 用`+`符号拼接**

用`+`拼接字符串如下：
`str = 'There are'+fruit1+','+fruit2+','+fruit3+' on the table'`
该方法效率比较低，不建议使用

#### **2. 用`%`符号拼接**
用`%`符号拼接方法如下：

`str = 'There are %s, %s, %s on the table.' % (fruit1,fruit2,fruit3)`

除了用元组的方法，还可以使用字典如下：

`str = 'There are %(fruit1)s,%(fruit2)s,%(fruit3)s on the table' % {'fruit1':fruit1,'fruit2':fruit2,'fruit3':fruit3}`
该方法比较通用


#### **3. 用`join()`方法拼接**

join()`方法拼接如下

``` python
	temp = ['There are ',fruit1,',',fruit2,',',fruit3,' on the table']
	''.join(temp)
```
该方法使用与序列操作

#### **4. 用`format()`方法拼接**

用`format()`方法拼接如下:

``` python
	str = 'There are {}, {}, {} on the table'
	str.format(fruit1,fruit2,fruit3)
```
还可以指定参数对应位置：

``` python
	str = 'There are {2}, {1}, {0} on the table'
	str.format(fruit1,fruit2,fruit3) #fruit1出现在0的位置
```

同样，也可以使用字典：

``` python
	str = 'There are {fruit1}, {fruit2}, {fruit3} on the table'
	str.format(fruit1=fruit1,fruit2=fruit2,fruit3=fruit3)
```

#### **5. 用`string`模块中的`Template`对象**
用`string`模块中的`Template`对象如下：

``` python
	from string import Template
	str = Template('There are ${fruit1}, ${fruit2}, ${fruit3} on the table') #此处用的是{}，别搞错了哦
	str.substitute(fruit1=fruit1,fruit2=fruit2,fruit3=fruit3) #如果缺少参数，或报错如果使用safe_substitute()方法不会
	str.safe_substitute(fruit1=fruit1,fruit2=fruit2) 
	#输出'There are apples, bananas, ${fruit3} on the table'
```

### **总结**
拼接的方法有多种，不同场合下使用不同的方法，个人比较推荐`%`、`format()`方法，简单方便。