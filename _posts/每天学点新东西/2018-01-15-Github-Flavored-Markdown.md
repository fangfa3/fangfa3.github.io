---
layout: post
title: "GitHub Flavored Markdown 常用格式"
date: 2018-01-15 21:50:00 
categories: 每天学点新东西
tag: markdown
---
* content 
{:toc}

GFM是Github拓展的基于Markdown的一种格式，在标准Markdown上做了少量修改。

### 表格
```
|姓名|学号|班级|
|-|-|-|
|张三|201221|B2|
|李四|201256|C3|
```

效果如下：

|姓名|学号|班级|
|-|-|-|
|张三|201221|B2|
|李四|201256|C3|


### 强调

`**加粗文本**` : **加粗文本**

`*斜体*` : *斜体*

`~~删了吧~~` : ~~删了吧~~

`**加粗了的_斜体_**` : **加粗了的_斜体_**

### 引用

```
>这是一个文本的引用。
```
效果如下：

>这是一个文本的引用。

```
在文中插入个小代码 `ctrl+v` 
```
效果如下：

在文中插入个小代码`ctrl+v`.

引用一段代码吧！

\`\`\` python
import numpy as np 
import tensorflow as tf 

a = 5
b = a + 5
print (b)
\`\`\`

效果：

``` python
import numpy as np 
import tensorflow as tf 

a = 5
b = a + 5
print (b)
```


\`\`\` cpp
\#include "qcustomplot"
\#include "QMessage"
\#include "QDebug"

int main ()
{
	qdebug()<<"hello"<<endl;
	return 0;
}
\`\`\`

效果如下：

``` cpp
#include "qcustomplot"
#include "QMessage"
#include "QDebug"

int main ()
{
	qdebug()<<"hello"<<endl;
	return 0;
}
```


### 链接

`[这里有个链接](https://fangfa3.github.io)` : [这里有个链接](https://fangfa3.github.io)

```
[这里有个一样的链接][1]

[1]:https://fangfa3.github.io
```

[这里有个一样的链接][1]

[1]:https://fangfa3.github.io


### 来个列表吧
```
* 一啊
* 二啊
* 三啊

- 第一
- 第二
- 第三

1. 第一步
  1. 首先
  2. 其次
  3. 最后
2. 第二步
3. 第三步
```

* 一啊
* 二啊
* 三啊

- 第一
- 第二
- 第三

1. 第一步
  1. 首先
  2. 其次
  3. 最后
2. 第二步
3. 第三步

### 图片

`![fishing bird.jpg](https://github.com/fangfa3/fangfa3.github.io/styles/images/scene/fishing_bird.jpg)`

效果如下：

![fishing bird.jpg](https://github.com/fangfa3/fangfa3.github.io/styles/images/scene/fishing_bird.jpg)

### 标题
```
# 标题一
标题一相关内容

## 标题二

这是标题二
### 标题三

标题三来


#### 标题四
标题四有点小
```

# 标题一
标题一相关内容

## 标题二

这是标题二
### 标题三

标题三来


#### 标题四
标题四有点小
