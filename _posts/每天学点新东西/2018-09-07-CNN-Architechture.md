---
layout: original
title: "CNN paper note"
date: 2018-09-07 21:50:00 
categories: 每天学点新东西
tag: CNN
---
* content 
{:toc}

### R-CNN

![R-CNN](https://github.com/fangfa3/fangfa3.github.io/blob/master/styles/images/AI/R-CNN.jpg?raw=true)

贡献：

提出了用卷积网络做检测。

提出了先用大的数据集预训练，再在目标任务的数据集上finetune。

具体地，CNN提取roi特征；`预测框修正`。


过程： 

1、对原图像运用Selective Search选出RoI(也可以叫Region Proposal, 预选框)；

2、把每个RoI resize后输入一个卷积网络里得到对应feature map；

3、一方面用全连接层修正预选框，一方面用SVM进行分类。

### SPPnet

![SPPnet](https://github.com/fangfa3/fangfa3.github.io/blob/master/styles/images/AI/SPPnet.jpg?raw=true)

贡献：

提出了 [RoI pooling](https://fangfa3.github.io/2018/09/06/RoIPooling-VS-RoIAlign/).


### Fast R-CNN

![Fast R-CNN](https://github.com/fangfa3/fangfa3.github.io/blob/master/styles/images/AI/Fast R-CNN.jpg?raw=true)

贡献：

1、用了`多任务损失函数`，分类+预测框修正；

2、训练时可以更新全部参数，不需存储faeture map。`这是与R-CNN对比`

过程：

1、对原图像运用Selective Search选出RoI(也可以叫Region Proposal, 预选框)；

2、把原图输入卷积网络中得到feature map。通过roi与对应的缩放比例得到roi的feature map。

3、对roi的feature map进行一次 RoI Pooling，得到固定大小的feature map。

4、经过全连接层进行分类+预测框修正。

### Faster R-CNN

![Faster R-CNN](https://github.com/fangfa3/fangfa3.github.io/blob/master/styles/images/AI/Faster R-CNN.JPG?raw=true)

贡献：`提出RPN`，用卷积网络得到RoI。


### Mask R-CNN
![Mask R-CNN](https://github.com/fangfa3/fangfa3.github.io/blob/master/styles/images/AI/Mask R-CNN.jpg?raw=true)

贡献：

1、 提出RoI Align

2、在Faster R-CNN基础上最后的输出加了一个mask的`损失函数`，`用于分割`。 