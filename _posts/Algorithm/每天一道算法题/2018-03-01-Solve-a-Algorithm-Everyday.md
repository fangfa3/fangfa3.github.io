---
layout: post
title: "每天一道算法题"
date: 2018-03-11 21:50:00 
categories: 每天一道算法题
tag: Algorithm
---
* content 
{:toc}

>**不积跬步无以至千里。 每天做一道算法题。**

<!--more-->



#### `2018.03.11` Two Sum

题目： 输入一个整数数组，返回相加之和等于给定值的两个数的序号（假设每个输入都有唯一解）

示例：

```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

解答：

``` python
class Solution:
	def twoSum(self, nums, target):
		"""
		:type nums: List[int]
		:type target: int 
		:rtype: List[int]
		"""
	d = {}
	for i, n in enumerate(nums):
		m = target - n
		if m in d:
			return [d[m], i]
		else: d[n] = i 	
```

知识点：

1、 enumerate()是python的内置函数。 对于一个可以遍历的对象（如列表、字符串等），enumerate()可将其组成一个索引序列，利用它可以同时获得索引和值。该函数多用在for循环中得到计数。

例如：

```
list1 = ["这", "是", "一个", "测试"]
for index, item in enumerate(list1):
    print index, item
>>>
0 这
1 是
2 一个
3 测试
```

同时，enumerate()还可以接收第二个参数，用于指定索引起始值，如：

```
list1 = ["这", "是", "一个", "测试"]
for index, item in enumerate(list1, 1):
    print index, item
>>>
1 这
2 是
3 一个
4 测试
```
