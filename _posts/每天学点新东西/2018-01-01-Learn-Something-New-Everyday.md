---
layout: post
title: "每天学点新东西 ———— 一月"
date: 2018-01-23 21:00:00   
categories: 每天学点新东西
tag: LSNE
---
* content
{:toc}

>**新模式说明：每天学习一个新的小技能或是解决一个小问题，花费时间20分钟即可，每天都在这一篇中进行更新。**

<!-- more -->

#### `2018.01.23` 伺服电机的三种控制方式

伺服电机是用于准确定位和频繁启停的高动态响应的机械设备。伺服电机有三种控制方式，位置控制方式、速度控制方式和转矩控制方式。

简单理解的话，位置控制方式就是通过控制电机运转的位置来控制伺服电机，让你转到什么位置你就转到什么位置；速度控制方式就是控制伺服电机运转的速度，让你以多快的速度转你就转多快；转矩控制方式是通过控制伺服电机的转矩来控制其运转，让你以多大的转矩转你就以多大的转矩转。

这里简单介绍一下转矩。转矩是转动力矩的简称，也就是一种力矩，力矩是作用力使物理绕着转动轴或支点转动的趋向。理解力矩可以联想推门的场景，一扇关着的门，从门把手处、中间位置和门内侧三个地方把门完全推开是需要不同的力的，最终把门完全推开，产生的力矩是一样的，因为力矩不仅与力有关，也与位移有关。

闲言少叙，回归正题。具体说一下三种控制方式。

位置控制方式，一般是通过外部输入的脉冲来控制。通过脉冲的频率来确定转动速度的大小，通过脉冲的个数来确定转动的角度。位置控制方式可以对速度和位置都有很严格的控制。

速度控制方式，通过外部模拟量的输入和脉冲的频率都可以进行转动速度的控制。

转矩控制方式，通过外部模拟量的输入来设定电机轴对外的输出转矩的大小。



#### `2018.01.20` A Simple Object Model —— 1

from [500 lines or less](http://aosabook.org/en/500L/a-simple-object-model.html)

``` python
def test_read_write_field():
	# Python code
	class A(object):
		pass
	obj = A()
	obj.a = 1
	assert obj.a == 1

	obj.b = 5
	assert obj.a == 1
	assert obj.b == 5

	obj.a = 2
	assert obj.a == 2
	assert obj.b == 5

	# Object model code 
#	A = Class(name="A", base_class=OBJECT, fields={}, metaclass=TYPE)
#	obj = Instance(A)
#	obj.write_attr("a", 1)
#	assert obj.read_attr("a") == 1
#
#	obj.write_attr("b", 5)
#	assert obj.read_attr("a") == 1
#	assert obj.read_attr("b") == 5
#
#	obj.write_attr("a", 2)
#	assert obj.read_attr("a") == 2
#	assert obj.read_attr("b") == 5

class Base(object)

	def __init__(self, cls, fields):
		self.cls = cls
		self.fields = fields

	def read_attr(self, fieldname):
		return self._read_dict(fieldname)

	def write_attr(self, fieldname, value):
		self._write_dict(fieldname, value)

	def isinstance(self, cls):
		return self.cls.issubclass(cls)

	def callmethod(self, methname, *args):
		meth = self.cls._read_from_class(methname)
		return meth(self, *args)

	def _read_dict(self, fieldname):
		return self._fields.get(fieldname, MISSING)

	def _write_dict(self, fieldname, value):
		self._fields[fieldname] = value

MISSING = object()
```



#### `2018.01.19` Chrome书签同步问题

*问题：*

在不同电脑上使用Chrome浏览器，发现有书签不同步的问题。明明之前在A电脑上添加了一个书签，换个地方，在B电脑上却没有同步，想要看之前添加的那个书签，又得花时间去找。

*解决：*

- 登录Chrome浏览器账户，在设置中找到同步选项，选择同步书签。
- 一个需要注意的点：登录Chrome账户时需要翻墙，在添加书签时也需要翻墙
- 再不行的话就先退出然后重新登录。

*总结一下解决方法就是：科学上网；重新登录*



