---
layout: post
title: "Hello Python"
date: 2018-03-13 21:00:00   
categories: python
tag: python
---
* content
{:toc}

>人生苦短，我用Python。



### Anaconda

#### Anaconda是什么？

Anaconda是一个用于科学计算的Python发行版，包含某一版本的Python和相关的配套工具。Anaconda可以利用conda这个工具/命令来进行包管理和环境管理。包管理就是你想用什么工具包，就可以安装相应的工具包。可以使用conda来安装、更新、卸载工具包，并且它更关注于数据科学相关的工具包。环境管理，指的是你可以设置多个python环境并选择使用。有的情况下你需要使用Python2，有的时候你需要Python3，在用Python3的时候经常用到一些工具包，都可以了利用conda来进行管理。

#### 为什么用Anaconda？

方便。Anaconda通过管理工具包、开发环境、Python版本，大大简化了我们的工作流程。

#### 如何使用Anaconda？

`工具包管理`

```
conda install numpy
conda update scipy
conda remove numpy
```

`环境管理`

假设默认的Python版本是3.5；那现在需要创建一个使用Python2.7的环境。用如下命令：

``` python
# 创建一个名为python27的环境，指定Python版本是2.7（不用管是2.7.x，conda会为我们自动寻找2.7.x中的最新版本）
conda create --name python27 python=2.7
 
# 安装好后，使用activate激活某个环境
activate python27 # for Windows
source activate python27 # for Linux & Mac
# 激活后，会发现terminal输入的地方多了python27的字样，实际上，此时系统做的事情就是把默认3.5环境从PATH中去除，再把2.7对应的命令加入PATH
 
# 此时，再次输入
python --version
# 可以得到`Python 2.7.6 :: Anaconda 5.1.1 (64-bit)`，即系统已经切换到了2.7的环境
 
# 如果想返回默认的python 3.5环境，运行
deactivate python27 # for Windows
source deactivate python27 # for Linux & Mac
 
# 删除一个已有的环境
conda remove --name python27 --all
```

#### 设置国内镜像

如果需要安装很多packages，你会发现conda下载的速度经常很慢，因为Anaconda.org的服务器在国外。所幸的是，清华TUNA镜像源有Anaconda仓库的镜像，我们将其加入conda的配置即可：

``` python
# 添加Anaconda的TUNA镜像
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
# TUNA的help中镜像地址加有引号，需要去掉
 
# 设置搜索时显示通道地址
conda config --set show_channel_urls yes
```


  






### python的安装

在[python官网](https://www.python.org/)下载对应于自己安装环境的安装包，Windows、Linux或是Mac的OSX系统，32位或64位，都可以找到对应的安装包。现在装的话建议装Python3，Python的核心团队计划于2020年停止支持Python2，既然Python2终将淘汰，那就没必要去学习了嘛。