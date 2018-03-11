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
|---|---:|:---:|
|张三|201221|B2|
|李四|201256|C3|
```

效果如下：

|姓名|学号|班级|
|---|---:|:---:|
|张三|201221|B2|
|李四|201256|C3|

<!-- more -->
### 强调

`**加粗文本**` : **加粗文本**

`*斜体*` : *斜体*

`~~删了吧~~` : ~~删了吧~~

### 公式

预览公式需要使用MathJax，所以需要先配置：开启Markdown Preview对MathJax的支持。配置方法是打开在 Markdown Preview 的用户配置文件 (Package Settings -> Markdown Preview -> Setting - User) 里添加如下内容：

```
{
	"enable_mathjax": true,
	"enable_highlight": true,
}
```

#### LaTex简明教程

先来看个例子：

```
$$ J(\theta) = \frac 1 2 \sum_{i=1}^m (h_\theta(x^{(i)})-y^{(i)})^2 $$
```
上面用LaTex格式书写的数学公式经过MathJax展示后效果如下：

$$ J(\theta) = \frac 1 2 \sum_{i=1}^m (h_\theta(x^{(i)})-y^{(i)})^2 $$

~~另外，行间公式使用`$$`作为公式的左右界限，行内公式使用`$`作为公式的左右界限。如$ \theta_i=\theta_i-\alpha\frac\partial{\\partial\theta_i}J(\theta) $~~

$$ \theta_i=\theta_i-\alpha\frac\partial{\\partial\theta_i}J(\theta) $$

更复杂的语法参考[Cmd Markdown 公式指导手册](https://www.zybuluo.com/codeep/note/163962)

#### 在github.io上显示

在根模板文件上增加一句话： 

```
<script type="text/javascript"
src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>
```

在我的Jekyll文件结构中，根模板的位置在_layout中。

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
2. 第二步
3. 第三步

### 图片

```
![fishing bird.jpg](https://github.com/fangfa3/
  fangfa3.github.io/blob/master/styles/images/scene/fishing_bird.jpg?raw=true)
```

效果如下：

![fishing bird.jpg](https://github.com/fangfa3/fangfa3.github.io/blob/master/styles/images/scene/fishing_bird.jpg?raw=true)

### 预览
在*Sublime Text* 下安装*Markdown Preview*插件。之后运用 *Alt* + *M* 快捷键即可在浏览器中预览。快捷键可修改：点击Preferences
--> 选择Key Bindings User 。

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
