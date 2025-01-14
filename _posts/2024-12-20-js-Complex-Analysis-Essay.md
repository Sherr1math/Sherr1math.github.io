---
layout: post
title: "Complex Analysis Essay"
subtitle: "The Final Homework of Complex Analysis II"
author: "Sherr1"
# header-style: text
header-img: "img/bg1.png"
catalog: true
mathjax: true
tags:
  - Complex Analysis
  - Essay
---
## Introduction
This is the essay of the Class "Complex Analysis II".

我写的这篇论文主题是关于三个经典积分命题及其推广.

## Abstract
留数定理巧妙地通过柯西积分定理将洛朗级数和积分计算巧妙结合在一起，为我们计算复杂
的广义积分乃至瑕积分提供了一种崭新的思路，极大降低了单纯地通过数学分析手段求解复杂积
分的难度。本文将结合自己这一个学期关于留数定理的学习以及阅读相关文献所积累下来的一些
关于留数定理的命题，从留数定理的视角去研究三个经典积分：欧拉积分、高斯积分、狄利克雷
积分及其推广形式

## Recalling
我们先来回顾一下留数定理：

关于**留数**的定义：

设 $z_0$ 是 $f(z_0)$ 的孤立奇点，于是 $f(z)$ 在 $ V(z_0,R)-\{z_0\} $ 中有**Laurent展开**

$$ \displaystyle f(z)=\sum_{k=-\infty}^{+\infty}c_k(z-z_0)^k,\quad z\in V(z_0,R)-\left\{z_0\right\} $$

此时

$$ \displaystyle c_{-1}=\frac{1}{2\pi i}\int_{\Gamma}f(z)dz $$

称为$f$在$z_0$处的**留数**，记为$Res(f,z_0)$.

关于**留数定理**的内容：

设$\Gamma$为一条正向简单闭路径，内部为$D$，$\{z_k\}_{1\leq k\leq n}$是$D$中有限个点，今若$f$在 $\bar{D}-\left\{z_k\right\}_{1\leq k\leq n}$ 上解析，则

$$ \frac{1}{2\pi i}\int_{\Gamma}f(z)dz=\sum_{k=1}^{n}Res(f,z_k) $$

关于在**极点处留数的计算方法**

设$a$是$f$的$n$阶极点，$n\geq1$.并设在$a$附近我们有$f(z)=\frac{g(z)}{(z-a)^n}$，其中$g(z)$在$a$解析且$g(a)\neq0$.则

$$ Res(f,a)=\frac{g^{(n-1)}(a)}{(n-1)!}$$

接着我们来研究以下几个经典的积分命题

### Euler Integral
**欧拉积分**这个例子来自南开数分教材第$19$章$B$组第$11$题.

对于$\forall \lambda>0,x>0,\alpha\in(-\frac{\pi}{2},\frac{\pi}{2})$，有
		$$
    \left\{
		\begin{aligned}
			\int_{0}^{+\infty}t^{x-1}e^{-\lambda t\cos\alpha}\cos(\lambda t\sin\alpha)dt=\frac{\Gamma(x)}{\lambda^x}\cos\alpha x\\
			\int_{0}^{+\infty}t^{x-1}e^{-\lambda t\cos\alpha}\sin(\lambda t\sin\alpha)dt=\frac{\Gamma(x)}{\lambda^x}\sin\alpha x
		\end{aligned}
		\right.
    $$

### Gauss Integral
**高斯积分(概率积分)**

$$I=\int_{-\infty}^{+\infty}e^{-x^2}dx=\sqrt{\pi}$$

我们也可以对高斯积分进行进一步的推广：

对于$\forall a,b\in\mathbb{C}$且$Re(a)>0$

$$ I(a,b)=\int_{-\infty}^{+\infty}e^{-ax^2+bx}dx=\sqrt{\frac{\pi}{a}}e^{\frac{b^2}{4a}} $$

在研究高斯积分的过程中，我们也可以发现**菲涅尔积分**公式：

$$ \int_0^\infty\sin x^2\mathrm{~}dx=\int_0^\infty\cos x^2\mathrm{~}dx=\sqrt{\frac\pi8} $$

同时我们也可以发现一些**Laplace逆变换**.

### Dirichlet Integral
狄利克雷积分这个例子来自南开复变教材第$4$章习题$33-(v),(vi)$.

$$ \int_{-\infty}^{+\infty}\frac{\sin x}{x}dx=\pi$$

更进一步，我们有其推广形式：

对$\forall m\in\mathbb{N}^{*}$，

$$
		\int_{-\infty}^{+\infty}\frac{\sin^m x}{x^m}dx=\left\{
		\begin{aligned}
		&\int_{-\infty}^\infty\frac{\sin^{2n+1}x}{x^{2n+1}}\mathrm dx=\frac{\pi}{(2n)!}\sum_{k=0}^n(-)^k\binom{2n+1}{k}\left(\frac{2n+1}{2}-k\right)^{2n}\quad m=2n+1\\
		&\int_{-\infty}^{\infty}\frac{\sin^{2n}x}{x^{2n}}\mathrm{d}x=\:\frac{\pi}{(2n-1)!}\sum_{k=0}^{n-1}(-1)^{k}\binom{2n}{k}(n-k)^{2n-1}\quad m=2n
		\end{aligned}\right.
$$

不过说实话这个狄利克雷积分挺搞的，复变函数期末考考，数学分析III期末考也考，结果我都算错了，太难绷了.

## Epilogue
留数定理堪称复变函数领域的一座巍峨丰碑。它犹如一条精妙的纽带，将复变函数在孤立奇点处看似微观局部的留数特性，与宏观层面的闭曲线积分紧密相连，展现出一种高屋建瓴的理论架构。在理论深度上，它是柯西积分定理等经典理论的卓越升华，极大地拓展了复变函数积分理论的边界，为深入探究函数在奇点附近的行为以及复杂区域上的积分开辟了崭新通途。其影响力更是跨越复变函数的范畴，在调和分析、数论等数学分支中若隐若现地编织起联系的网络，促进了数学学科内部的深度交融。

正如高斯所言：“数学中的一些美丽定理具有这样的特性：它们极易从事实中归纳出来，但证明却隐藏的极深。” 留数定理便是这样一个美丽且深刻的定理，它建立了函数在孤立奇点处的留数与闭曲线积分之间的联系，这种联系看似简洁明了，但背后的证明和理论基础却蕴含着深刻的数学思想。

## Partial content display:
![](/img/in-post/math/Essay/Complex%20Analysis%20II%20Essay/Page_1.jpg)

## Download for PDF
For more information about this essay, please refer to the following sources(Chinese version):

Click [Here](/files/Essay/复变II期末论文.pdf) to get my essay.

## Remark
If you have any questions or need further assistance, feel free to ask! Here is my email: [nkusherr1 at gmail.com](mailto:nkusherr1@gmail.com)
