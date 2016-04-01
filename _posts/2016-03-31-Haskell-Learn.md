---
layout: post
title: Haskell趣学指南 -- 初试
categories: [blog ]
tags: [Haskell, Coding, ]
description: Haskell趣学指南
---

# 安装

```bash
sudo apt-get install rhythmbox-plugins
sudo apt-get install haskell-platform
```

# 简单测试

&emsp;首先编辑一个小脚本:
```
anderson@Peacesky:~$ cat .ghci
:set prompt "ghci>"
```
&emsp;这样只是产生了这样的改变：

```
anderson@Peacesky:~$ ghci
GHCi, version 7.10.3: http://www.haskell.org/ghc/  :? for help
Prelude>
```

<center>$\Downarrow$ &emsp;$\Downarrow$ &emsp;$\Downarrow$ &emsp;$\Downarrow$ &emsp;$\Downarrow$

```
anderson@Peacesky:~$ ghci
GHCi, version 7.10.3: http://www.haskell.org/ghc/  :? for help
ghci>
```

## 测试数字加减

```haskell
ghci> 3 + 15
18
ghci> 4.0 + 16
20.0
ghci> 4.0 + 16.3
20.3
ghci> 4.0 + 16.35
20.35
```

## 测试包含优先级的加减乘除

```haskell
ghci> 4.0 * (5 - 6)
-4.0
```
## 测试逻辑运算
```
ghci>True && True
True
ghci>True && False
False
ghci>True || False
True

ghci> 5 == 4
False
ghci> 5 /= 4
True
ghci> 4 == 4
True
ghci> "hello" == "hello"
True

ghci> 5 + "hello"

<interactive>:22:4:
    No instance for (Num [Char]) arising from a use of ‘+’
    In the expression: 5 + "hello"
    In an equation for ‘it’: it = 5 + "hello"

```

# 1.1. 调用函数

<br/>&emsp;写一个简单的小函数；
```haskell
anderson@Peacesky:~/Code/Haskll$ cat baby.hs
doubleMe x = x + x
doubleUs x y = x * 2 + y * 2
doubleThem x y = doubleMe x + doubleMe y
```

测试:
```
# 读取函数
ghci>:l baby
[1 of 1] Compiling Main             ( baby.hs, interpreted )
Ok, modules loaded: Main.
# 调用
ghci>doubleMe 16
32
ghci>doubleUs 16 12
56
ghci>doubleThem 1.2 3.5
9.4
```
再写一个含有if的语句:
```
doubleSmallNumber x = if x > 100
                      then x
                      else x*2
```
Haskell的if语句的与众不同之处在于,else部分是**不可省略的!**
因为在Haskell中,**程序是一系列函数的集合**:函数取数据作为参数,并将他们转为想要的结果.
**既然必须返回结果,不管条件满足还是失败,都需要返回一个结果.**
一言以蔽之,Haskell中的if是一个必然返回结果的表达式(expression).而非语句.(statment).





