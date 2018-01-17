---
layout: post
title: "python学习-面向对象编程"
date: 2018-01-17 21:00:00   
categories: python
tag: python
---
* content
{:toc}

学习用`python`写了个简单的面向对象的程序。

<!-- more -->

``` python
class myclass:
	classname = "python learning"

	def __init__(self, name1, age1): #构造方法
		self.name = name1
		self.age = age1
		print ("hello")

	def speak(self): #实例方法
		intro = "this is def speak. " + self.name + "说：我今年" + str(self.age) + "岁。" 
		print (intro)

obj1 = myclass("fangfa3", 22)
obj2 = myclass("hahh", 23)

print (obj1.name)
print (obj1.age)
print (obj2.classname)

obj2.speak()

class hisclass(myclass): #继承
	def speak(self):
		print ("我们不一样")

obj3 = hisclass("his",33)
print (obj3.name, obj3.age)
obj3.speak()
```

执行结果如下：

![first_oop.jpg](https://github.com/fangfa3/fangfa3.github.io/blob/master/styles/images/python/first_oop.JPG?raw=true)

*需要注意几点：*

- `__init__`为构造方法，在类创造对象时自动执行。其第一个参数必须是`self`，为实例化的对象本身。 `__init__`前后分别有两个下划线。
- 实例方法需要实例化的对象调用。
- 继承实现了代码的重用，可以在一定的基础上修改，减少代码的重新编写。