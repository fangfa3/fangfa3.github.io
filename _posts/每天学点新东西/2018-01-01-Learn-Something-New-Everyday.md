---
layout: post
title: "每天学点新东西 ———— 一月"
date: 2018-01-19 21:00:00   
categories: 每天学点新东西
tag: LSNE
---
* content
{:toc}

>**新模式说明：每天学习一个新的小技能或是解决一个小问题，花费时间20分钟即可，每天都在这一篇中进行更新。**

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

<!-- more -->

#### `2018.01.19` Chrome书签同步问题

*问题：*

在不同电脑上使用Chrome浏览器，发现有书签不同步的问题。明明之前在A电脑上添加了一个书签，换个地方，在B电脑上却没有同步，想要看之前添加的那个书签，又得花时间去找。

*解决：*

- 登录Chrome浏览器账户，在设置中找到同步选项，选择同步书签。
- 一个需要注意的点：登录Chrome账户时需要翻墙，在添加书签时也需要翻墙
- 再不行的话就先退出然后重新登录。

*总结一下解决方法就是：科学上网；重新登录*



