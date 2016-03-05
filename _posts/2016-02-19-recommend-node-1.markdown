---
layout: post
title: 《推荐系统入门》笔记
categories: [blog ]
tags: [DataMining, ]
description: 推荐系统入门
---
## 社会化协同过滤
首先，如何找到相似的用户？
![](http://7xriwb.com1.z0.glb.clouddn.com/1751516254.png)

X先生：
### 1. 曼哈顿距离
(x<sub>1</sub>, y<sub>1</sub>)表示艾米，(x<sub>2</sub>, y<sub>2</sub>)表示那位神秘的X先生，那么他们之间的曼哈顿距离就是：
|x<sub>1</sub> - x<sub>2</sub>| + |y<sub>1</sub> - y<sub>2</sub>|
也就是x之差的绝对值加上y之差的绝对值，这样他们的距离就是4。
![](http://7xriwb.com1.z0.glb.clouddn.com/406934215.png)
完整的计算结果如下：
![](http://7xriwb.com1.z0.glb.clouddn.com/225742177.png)

    艾米的距离最近，在她的浏览历史中可以看到她曾给巴奇加卢比的《发条女孩》打过五星，于是我们就可以把这本书推荐给X先生。
    曼哈顿距离的优点之一是计算速度快，对于Facebook这样需要计算百万用户之间的相似度时就非常有利。
### 2. 欧几里得距离
### 勾股定理

也许你还隐约记得勾股定理。另一种计算距离的方式就是看两点之间的直线距离：
![](http://7xriwb.com1.z0.glb.clouddn.com/1549028541.png)
    利用勾股定理，我们可以如下计算距离：
![](http://7xriwb.com1.z0.glb.clouddn.com/110435117.png)
    这条斜线就是欧几里得距离，公式是：
$\sqrt{(x<sub>1</sub> - x<sub>2</sub>)<sup>2</sup> + (y<sub>1</sub> - y<sub>2</sub>)<sup>2</sup>}$

    回顾一下，这里的x1表示用户1喜欢《龙纹身》的程度，x2是用户2喜欢这本书的程度；y1则是用户1喜欢《雪崩》的程度，y2是用户2喜欢这本书的程度。
    艾米给《龙纹身》和《雪崩》都打了五颗星，神秘的X先生分别打了两星和四星，这样他们之间的欧几里得距离就是：
$\sqrt{(5 - 2)<sup>2</sup> + (5 - 4)<sup>2</sup>}$ = $\sqrt{3<sup>2</sup> + 1<sup>2</sup>}$

