---
layout: original
title: "轻量级CNN"
date: 2018-08-08 21:50:00 
categories: 每天学点新东西
tag: Paper Note
---
* content 
{:toc}


##  ShuffleNetV2

### FLOP

FLOP全称为floating point operation，意指浮点计算量，理解为计算量，可以用来衡量算法/模型的复杂度。(`TODO:` 如何计算FLOP)

### 轻量级网络设计四条指导原则：

#### 1、Equal channel width minimizes memory access cost (MAC).

相同的通道数可以减小内存访问消耗时间(MAC).

#### 2、Excessive group convolution increases MAC.

过度的组卷积会增加MAC。

#### 3、Network fragmentation reduces degree of parallelism.

网络分支减小并行度。

#### 4、Element-wise operations are non-negligible.

逐个元素的运算律也不可忽视。

#### 总结

Based on the above guidelines and empirical studies, we conclude that an efficient network architecture should 
1) use "balanced" convolutions (equal channel width); 
2) be aware of the cost of using group convolution;
3) reduce the degree of fragmentation;
4) reduce element-wise operations. 
These desirable properties depend on platform characterics (such as memory manipulation and code optimization) that are beyond theoretical FLOPs. They should be taken into accout for practical network design.

### 基础知识

#### down sampling 下采样

下采样指的是将图片缩小一定比例，一般采用平均池化层来实现。

注：对应地，上采样是指将图片放大一定比例，一般通过插值算法来实现。

#### Batch Normalization

作用：极大提升训练速度，收敛过程大大加快；同时能增加分类效果；使调参过程更加简单。

算法：输入mini-batch，输出经过归一化的x和y。

实际使用(Keras): model.add(BatchNormalization())；先BN再ReLU

#### Group Convolution

最早在AlexNet中使用，是为了解决显存不够的问题，将网络部署在两张GTX 580显卡上训练，Alex认为group conv的方式能够增加 filter之间的对角相关性，而且能够减少训练参数，不容易过拟合，这类似于正则的效果。

具体操作见图：

下图为普通的卷积操作：
![normal_convolution](https://github.com/fangfa3/fangfa3.github.io/blob/master/styles/images/AI/normal_convolution.jpg?raw=true)

对应地，下图为组卷积操作：
![group_convolution](https://github.com/fangfa3/fangfa3.github.io/blob/master/styles/images/AI/group_convolution.jpg?raw=true)

#### Depthwise Convolution

MobileNets可以在基本保证准确率的前提下大大减少计算时间和参数数量。

MobileNets将普通的卷积操作分解为两步，第一步是depthwise convolution，用M个维度为DK\*DK\*1的卷积核去卷积对应输入的M个feature map, 即DF\*DF\*M；第二步是pointwise convolution,用N个1\*1\*M的卷积核去卷积第一步的结果，得到与普通卷积相同的大小，即DF\*DF\*N。

具体见下图：
![MobileNets](https://github.com/fangfa3/fangfa3.github.io/blob/master/styles/images/AI/depthwise_convolution.jpg?raw=true)

### 总体框架

#### Review of ShuffleNet V1

Channel Shuffle 示意图：
![ShuffleNet_channel_shuffle](https://github.com/fangfa3/fangfa3.github.io/blob/master/styles/images/AI/ShuffleNet_channel_shuffle.jpg?raw=true)

A 'channel shuffle' operation is then introduced to enable information communication between different groups of channels and improve accuracy. 

ShuffleNet V1组成单元：
![ShuffleNet_unit](https://github.com/fangfa3/fangfa3.github.io/blob/master/styles/images/AI/ShuffleNet_unit.jpg?raw=true)


ShuffleNet V1 总体框架：
![ShuffleNet_overall](https://github.com/fangfa3/fangfa3.github.io/blob/master/styles/images/AI/ShuffleNet_overall.jpg?raw=true)

#### ShuffleNet V2

ShuffleNet V2组成单元：
![ShuffleNetV2_unit](https://github.com/fangfa3/fangfa3.github.io/blob/master/styles/images/AI/ShuffleNetV2_unit.jpg?raw=true)


ShuffleNet V2 总体框架：
![ShuffleNetV2_overall](https://github.com/fangfa3/fangfa3.github.io/blob/master/styles/images/AI/ShuffleNetV2_overall.jpg?raw=true)