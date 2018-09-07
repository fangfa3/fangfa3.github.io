---
layout: original
title: "RoIPooling VS RoIAlign"
date: 2018-09-06 21:50:00 
categories: 每天学点新东西
tag: markdown
---
* content 
{:toc}

[参考](http://blog.leanote.com/post/afanti.deng@gmail.com/b5f4f526490b)

### RoI Pooling

对于不同大小feature map的输入可以有一定大小的输出。

缺点：过程中有两次量化，会发生小小的偏移。因此在Mask R-CNN中提出了RoI Align。

### RoI Align

取消roi pooling过程中的两次量化，在spatial bin中运用双线性插值法找出采样点的像素值进行pooling。
