---
layout: post
title: "递归算法"
date: 2018-04-13 21:00:00   
categories: Algorithm
tag: Algorithm
---
* content
{:toc}


### 概念

递归： 程序调用自身。运用递归通常可以把一个大型的复杂问题转化为一个与原问题相似的规模较小的问题来解决，代码简洁易懂。

迭代： 利用变量的原值推算出变量的新值。一般是用循环实现。

<!-- more -->

### 设计思路

大部分情况下，递归和迭代可以相互转换。但是二者的设计思路有所差异。

直接看个例子：要求一个数字串所有的组合方式，只能按顺序一个数字或两个数字组合。

``` python
#输入`1234`， 输出
#[1, 2, 3, 4]
#[1, 2, 34]
#[1, 23, 4]
#[12, 3, 4]
#[12, 34]
```

``` python
#递归思路：一个数字串，从头开始看，要么是第一个单独为一个，要么是第一个和第二个合并为一个；
#这两种不管选择哪一种之后还会剩下一个数字串，对这个剩下的数字串继续这样的操作。
#当然，每一步都要判断下条件，比如说剩下的字符串长度必须大于2才能将两个合并。最后数字串没有了就输出一个结果。

import copy
class Solution:
	def Find(self, s): #s为输入的数字串
		result = [] #定义一个空列表，方便递归
		self.Permutation(result, s) # 进入递归

	def Permutation(self, result, tr):
		if not tr:  #数字串为空，即代表递归结束，输出对应结果。
			print(result)
			return
		if len(tr) >= 1:  #数字串长度大于1时，将该字符串的第一个单独加入结果列表
			temp1 = copy.copy(result)
			temp1.append(int(tr[0]))
			self.Permutation(temp1, tr[1:]) #对剩下的数字串继续重复
		if len(tr) >= 2:  #数字串长度大于2时，将该字符串的前两个合并加入结果列表
			temp2 = copy.copy(result)
			temp2.append(int(tr[0]+tr[1]))
			self.Permutation(temp2, tr[2:]) #对剩下的数字串继续重复

```

``` python
#迭代思路：对数字串从头往后一个一个看，第一个数直接加入结果列表，从第二个数之后，每个数都有两种选择，要么自己单独加入结果列表，要么和结果列表中的前一个数合并
#合并的情况有个条件：结果列表的最后一个数必须只有一位（因为题目要求最多只能两位一起组合）
s = list(input().strip())

def process(s):
    if len(s) < 2:
        return s
    res = [[s[0]]]
    for i in range(1, len(s)):
        tmp = []
        while res:
            cur = res.pop()
            tmp.append(cur + [s[i]])
            if len(cur[-1]) == 1:
                cur[-1] += s[i]
                tmp.append(cur)
        res = tmp
    return res
```

递归：通常对问题整体考虑，分为两部分，前一部分结合具体问题设计，后一部分作为一个整体又可以使用之前的分析方法。

迭代：逐个考虑， 第一个是什么样的，第二个在第一个的基础上如何变化，第三个在第二个的基础上如何变化，找出规律，写出代码。


### 典型问题

#### 斐波那契数列

一般介绍递归时，都会介绍斐波那契数列。 这十分有利于对递归的理解。

**一般地，问题是有多少种方法之类的，可以联想到斐波那契数列，或者说是递归。先从最简单情况考虑起，最终得到相应的表达式**
变量为1时，有几种方法，变量为2时，是否可以分解为与变量为1时相关的子方法。依次下去，寻找规律。 

虽然斐波那契数列有助于理解递归，但**编程时一般不用递归写**。因为：

* 如果将递归具体的计算展开就会发现，有大量的重复计算，增加了运算时间；

* 递归会不断的调用栈，如果递归深度很深，会引起内存栈溢出，这是很严重的问题。

``` python
# 题目描述
# 一只青蛙一次可以跳上1级台阶，也可以跳上2级。求该青蛙跳上一个n级的台阶总共有多少种跳法。

class Solution:
    def jumpFloor(self, number):
        # 迭代:
        jumpMethods = []
        for i in range(1,number+1):
            if i == 1:
                jumpMethods.append(1)
                continue
            if i == 2:
                jumpMethods.append(2)
                continue
            jumpMethods.append(jumpMethods[i-2]+jumpMethods[i-3])
        return jumpMethods[number-1]

    def jumpFloor2(self, number)
        # 递归:
        if number == 1:
          return 1
        if number == 2:
          return 2
        return self.jumpFloor(number-1) + self.jumpFloor(number-2)

```

#### 二叉树

由于树的定义就使用了递归，很多情况下二叉树的问题都会用到递归。一方面是针对具体的问题具体解决，另一方面找到新的根节点进行递归。



