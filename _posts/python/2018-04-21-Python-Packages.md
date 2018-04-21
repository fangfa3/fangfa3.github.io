---
layout: post
title: "数据分析中Python的常用库介绍"
date: 2018-04-21 21:00:00   
categories: python
tag: python
---
* content
{:toc}

>Get your hands dirty.

[本文参考](https://www.zhihu.com/question/37180159/answer/96682815)

数据分析、机器学习中常用的库有这些： pandas, numpy, scipy, matplotlib, scikit-learn。简而言之，pandas用来做**数据处理**，numpy用来做**高纬度矩阵运算**，scipy用来做**科学计算**，matplotlib用来做**数据可视化**，scikit-learn用来做**机器学习和数据挖掘**.

<!-- more -->

### `Numpy`

来存储和处理大型矩阵，比Python自身的嵌套列表（nested list structure)结构要高效的多，本身是由C语言开发。这个是很基础的扩展，其余的扩展都是以此为基础。数据结构为ndarray,一般有三种方式来创建。

### `Pandas`

基于NumPy 的一种工具，该工具是为了解决数据分析任务而创建的。Pandas 纳入了大量库和一些标准的数据模型，提供了高效地操作大型数据集所需的工具。最具有统计意味的工具包，某些方面优于R软件。数据结构有一维的Series，二维的DataFrame(类似于Excel或者SQL中的表，如果深入学习，会发现Pandas和SQL相似的地方很多，例如merge函数)，三维的Panel。
