---
layout: post
title: "Mathematical Analysis III Mid-Test"
subtitle: "Mathematical Analysis III Mid-Test of Nankai University (Boling Version)"
author: "Sherr1"
# header-style: text
header-img: "img/bg6.png"
catalog: true
mathjax: true
tags:
  - Analysis Problems
  - Series Problems
  - Nankai University
  - Exam
---

## Introduction
This is the **Midterm Exam of Mathematical Analysis III**(Boling Class) at Nankai University in the autumn semester of 2024-2025.

On the whole, the difficulty level of this test is between that of last year and the year before.
## Problems and Solutions
#### Exercise 1
研究下列级数的收敛性

$$(1)\quad\displaystyle\sum_{n=1}^{+\infty}\frac{\sin(n+\frac{1}{n})}{\sqrt{n}}$$

$$(2)\quad\displaystyle\sum_{n=1}^{+\infty}\Big(\big(1+\frac{1}{n+1}\big)^{2n}-\big(1+\frac{2}{n+a}\big)^{n}\Big)$$

##### Solution 1-(1)-1
已知$\displaystyle\sum_{n=1}^{+\infty}\frac{\sin n}{\sqrt{n}}$ 收敛，考虑：

$$\displaystyle\sum_{n=1}^{+\infty}\frac{\sin(n+\frac{1}{n^2})}{\sqrt{n}}-\sum_{n=1}^{+\infty}\frac{\sin n}{\sqrt{n}}=\sum_{n=1}^{+\infty}\frac{\sin(n+\frac{1}{n^2})-\sin n}{\sqrt{n}}=\sum_{n=1}^{+\infty}\frac{\cos\theta_n}{n^2\sqrt{n}}$$

又

$$\sum_{n=1}^{+\infty}\left|\frac{\cos\theta_n}{n^2\sqrt{n}}\right|\leq\sum_{n=1}^{+\infty}\frac{1}{n^2\sqrt{n}}$$

而$\displaystyle\sum_{n=1}^{+\infty}\frac{1}{n^2\sqrt{n}}$收敛，故$\displaystyle\sum_{n=1}^{+\infty}\left|\frac{\cos\theta_n}{n^2\sqrt{n}}\right|$收敛，故$\displaystyle\sum_{n=1}^{+\infty}\frac{\cos\theta_n}{n^2\sqrt{n}}$收敛，即有$\displaystyle\sum_{n=1}^{+\infty}\frac{\sin(n+\frac{1}{n^2})}{\sqrt{n}}$收敛.

##### Solution 1-(1)-2
$$\displaystyle\sum_{n=1}^{+\infty}\frac{\sin(n+\frac{1}{n^2})}{\sqrt{n}}=\sum_{n=1}^{+\infty}\frac{\sin n\cos\frac{1}{n^2}}{\sqrt{n}}+\sum_{n=1}^{+\infty}\frac{\cos n\sin\frac{1}{n^2}}{\sqrt{n}}$$

由于$\displaystyle\sum_{n=1}^{+\infty}\frac{\sin n}{\sqrt{n}}$收敛，$\displaystyle\cos\frac{1}{n^2}$单调有界，故由\textbf{Abel判别法}可知$\displaystyle\sum_{n=1}^{+\infty}\frac{\sin n\cos\frac{1}{n^2}}{\sqrt{n}}$收敛.

由于$\displaystyle\left|\frac{\cos n\sin\frac{1}{n^2}}{\sqrt{n}}\right|\leq\left|\frac{sin\frac{1}{n^2}}{\sqrt{n}}\right|\leq\frac{1}{n^2\sqrt{n}}$且$\displaystyle\sum_{n=1}^{+\infty}\frac{1}{n^2\sqrt{n}}$收敛，故$\displaystyle\sum_{n=1}^{+\infty}\frac{\cos n\sin\frac{1}{n^2}}{\sqrt{n}}$收敛.

又由于
    $$\displaystyle\sum_{n=1}^{+\infty}\frac{\sin(n+\frac{1}{n^2})}{\sqrt{n}}=\sum_{n=1}^{+\infty}\frac{\sin n\cos\frac{1}{n^2}}{\sqrt{n}}+\sum_{n=1}^{+\infty}\frac{\cos n\sin\frac{1}{n^2}}{\sqrt{n}}$$

故$\displaystyle\sum_{n=1}^{+\infty}\frac{\sin(n+\frac{1}{n^2})}{\sqrt{n}}$收敛.

##### Solution 1-(2)
$$\begin{aligned}
    &(1+\frac{1}{n+1})^{2n}-(1+\frac{2}{n+a})^n=e^{2n\ln\left(1+\frac{1}{n+1}\right)}-e^{\ln\left(1+\frac{2}{n+a}\right)}\\
    =&e^{2n\left(\frac{1}{n+1}-\frac{1}{2(n+1)^2}+o(\frac{1}{n^2})\right)}-e^{n\left(\frac{2}{n+a}-\frac{4}{2(n+a)^2}+o(\frac{1}{n^2})\right)}\\
    =&e^2{\left(e^{\frac{2n}{n+1}-2-\frac{n}{(n+1)^2}+o(\frac{1}{n})}-e^{\frac{2n}{n+a}-2-\frac{2n}{(n+a)^2}+o(\frac{1}{n})}\right)}\\
    =&e^2\left(1-\frac{2}{n+1}-\frac{n}{(n+1)^2}+o(\frac{1}{n^2})-1+\frac{2a}{n+a}+\frac{2n}{(n+a)^2}+o(\frac{1}{n^2})\right)\\
    =&e^2\left(\frac{2a(n+1)-2(n+a)}{(n+1)(n+a)}+\frac{2}{n}-\frac{1}{n}+o(\frac{1}{n})\right)=e^2\left(\frac{2a-2+1}{n}+o(\frac{1}{n})\right)\sim e^2\frac{2a-1}{n}
    \end{aligned}$$
    由上式可知当且仅当$2a-1=0\Rightarrow a=\frac{1}{2}$时收敛，其余情况均发散.

#### Exercise 2
判断下列积分的收敛性

$$\iint_{x^2+y^2\geq1}\frac{\cos(x^2)}{x^2+y^2}dxdy$$

##### Solution 2-1
首先我们有**广义积分的绝对收敛和收敛是等价的**，故我们只需研究下列积分的收敛性即可：

$$\iint_{x^2+y^2\geq1}\frac{\left|\cos(x^2)\right|}{x^2+y^2}dxdy$$

由于

$$\frac{\left|\cos(x^2)\right|}{x^2+y^2}\geq\frac{1}{2(x^2+y^2)}+\frac{\cos(2x^2)}{2(x^2+y^2)}$$

故

$$\iint_{x^2+y^2\geq1}\frac{\left|\cos(x^2)\right|}{x^2+y^2}dxdy\geq\iint_{x^2+y^2\geq1}\frac{1}{2(x^2+y^2)}dxdy+\iint_{x^2+y^2\geq1}\frac{\cos(2x^2)}{2(x^2+y^2)}dxdy$$

**反证**：我们假设原积分收敛，则有：

$$\iint_{x^2+y^2\geq1}\frac{\left|\cos(x^2)\right|}{x^2+y^2}dxdy\text{与}\iint_{x^2+y^2\geq1}\frac{\cos(2x^2)}{2(x^2+y^2)}dxdy\text{均收敛}$$

进而有

$$\iint_{x^2+y^2\geq1}\frac{1}{2(x^2+y^2)}dxdy\text{收敛}$$

而

$$\iint_{x^2+y^2\geq1}\frac{1}{2(x^2+y^2)}dxdy=\int_{0}^{2\pi}d\theta\int_{1}^{+\infty}\frac{r}{2r^2}dr=\pi\int_{1}^{+\infty}\frac{1}{r}dr\text{发散}$$

故矛盾，即$\displaystyle\iint_{x^2+y^2\geq1}\frac{\cos(x^2)}{x^2+y^2}dxdy$发散.

##### Solution 2-2
$$\iint_{x^2+y^2\geq1}\frac{\left|\cos(x^2)\right|}{x^2+y^2}dxdy=\lim_{A\rightarrow+\infty}\int_{0}^{2\pi}d\theta\int_{1}^{A}\frac{\left|\cos(r^2\cos^2\theta)\right|}{r^2}rdr\quad(\clubsuit)$$

令$r=\frac{\sqrt{t}}{\left|\cos\theta\right|}$，则$dr=\frac{1}{2\sqrt{t}}\frac{1}{\left|\cos\theta\right|}$，代入$(\clubsuit)$式，我们有：

$$\lim_{A\rightarrow+\infty}\int_{0}^{2\pi}d\theta\int_{1}^{A}\frac{\left|\cos(r^2\cos^2\theta)\right|}{r^2}rdr\geq\lim_{A\rightarrow+\infty}\int_{0}^{2\pi}d\theta\int_{1}^{\frac{1}{2}A^2}\frac{\left|\cos t\right|}{\frac{\sqrt{t}}{\left|\cos\theta\right|}}\frac{1}{2\sqrt{t}}\frac{1}{\left|\cos\theta\right|}\geq2\pi\int_{1}^{\frac{1}{2}A^2}\frac{\left|\cos t\right|}{t}dt\quad\text{发散}$$

故$\displaystyle\iint_{x^2+y^2\geq1}\frac{\cos(x^2)}{x^2+y^2}dxdy$发散.

#### Exercise 3
研究下列积分的收敛性

$$\int_{0}^{+\infty}\frac{x^q}{1+x^p}\cos xdx$$

##### Solution 3
可能的奇点：$0,+\infty$

$$\int_{0}^{+\infty}\frac{x^q}{1+x^p}\cos xdx=\int_{0}^{1}\frac{x^q}{1+x^p}\cos xdx+\int_{1}^{+\infty}\frac{x^q}{1+x^p}\cos xdx$$

在$x=0$处，$\displaystyle\frac{x^q}{1+x^p}\cos x\sim x^q(x\rightarrow0^{+})\Rightarrow q\gt-1$收敛.

在$x\rightarrow+\infty$处，

$$\int_{1}^{+\infty}\frac{x^q}{1+x^p}\cos xdx=\int_{1}^{+\infty}\frac{x^p}{1+x^p}x^{q-p}\cos xdx$$

显然由$Cauchy$判别法易知$q-p\geq0$发散.

当$q-p\lt-1$时，

$$\int_{1}^{+\infty}\left|\frac{x^p}{1+x^p}x^{q-p}\cos x\right|dx\leq\int_{1}^{+\infty}x^{q-p}dx\quad\text{收敛}$$

即此时有$\displaystyle\int_{1}^{+\infty}\frac{x^q}{1+x^p}\cos xdx$绝对收敛.

当$-1\leq q-p\lt0$时，

$$\left|\frac{x^p}{1+x^p}x^{q-p}\cos x\right|\geq\frac{1}{2}x^{q-p}\cos^2x=\frac{1}{4}x^{q-p}(1+\cos 2x)=\frac{1}{4}x^{q-p}+\frac{1}{4}x^{q-p}\cos 2x$$

而$\displaystyle\int_{1}^{+\infty}\frac{1}{4}x^{q-p}dx$发散，$\displaystyle\int_{1}^{+\infty}\frac{1}{4}x^{q-p}\cos 2xdx$由$Dilichlet$判别法易知收敛，故

$$\int_{1}^{+\infty}\left|\frac{x^p}{1+x^p}x^{q-p}\cos x\right|dx\geq\int_{1}^{+\infty}\frac{1}{4}x^{q-p}dx+\int_{1}^{+\infty}\frac{1}{4}x^{q-p}\cos 2xdx\quad\text{发散}$$

故此时有$\displaystyle\int_{1}^{+\infty}\frac{x^q}{1+x^p}\cos xdx$条件收敛.

综上：

$$\left\{\begin{aligned}
        q-p\lt-1\text{且}q\gt-1&\quad\text{绝对收敛}\\
        -1\leq q-p\lt0\text{且}q\gt-1 &\quad\text{条件收敛}\\
        q-p\geq0\text{或}q\leq-1 &\quad\text{发散}
    \end{aligned}\right.$$

#### Exercise 4
设$p\geq0$，数列$a_n$满足$a_1=1,a_{n+1}=n^{-p}\arctan a_n$，判断并证明级数

$$\sum_{n=1}^{\infty}a_n$$

的收敛性

##### Solution 4

①$p\gt0$时，

$$\arctan x\sim x(x\rightarrow0)\quad\frac{a_{n+1}}{a_n}\sim n^{-p}\rightarrow0(n\rightarrow\infty)$$

由达朗贝尔判别法知**收敛**.

②$p=0$时，

$$a_{n+1}=\arctan a_n\quad\arctan x\sim x-\frac{1}{3}x^3+o(x^3)$$

$$\lim_{n\rightarrow\infty}\frac{a_n^r}{n}=\lim_{n\rightarrow\infty}\frac{a_{n+1}^r-a_n^r}{n+1-n}=\lim_{n\rightarrow\infty}\frac{r\theta_n^{r-1}(a_{n+1}-a_n)}{1}=\lim_{n\rightarrow\infty}ra_n^{r-1}(-\frac{1}{3}a_n^3)=-\frac{r}{3}\lim_{n\rightarrow\infty}a_n^{r+2}$$

取$r=-2$有$\lim_{n\rightarrow\infty}\frac{a_n^{-2}}{n}=\frac{2}{3}\Rightarrow a_n\sim\sqrt{\frac{2}{3n}}\Rightarrow\sum_{n=1}^{+\infty}a_n$\textbf{发散}.

#### Exercise 5
判断下列积分的收敛性

$$\int_{0}^{+\infty}(-1)^{\left[x^3\right]}dx$$

##### Solution 5
显然这是一个**非绝对收敛**的积分.
    $$\int_{0}^{+\infty}(-1)^{\left[x^3\right]}dx=\sum_{n=0}^{+\infty}\int_{\sqrt[3]{n}}^{\sqrt[3]{n+1}}(-1)^ndx=\sum_{n=0}^{+\infty}\left((n+1)^{\frac{1}{3}}-n^{\frac{1}{3}}\right)(-1)^n=\sum_{n=0}^{+\infty}\frac{1}{3\sqrt[3]{\theta_n^2}}$$
    其中$n\leq\theta_n\leq n+1$，故由$Libiniz$判别法知收敛，即$\displaystyle\int_{0}^{+\infty}(-1)^{\left[x^3\right]}dx$**条件收敛**.

#### Exercise 6
设$G$为$\mathbb{R}^2$上的有界闭区域，$\partial G$由有线条分段光滑的简单闭曲线构成，假设$u\in C^2(G)$，且$u$在边界上恒为$0$，证明对$\forall\lambda\gt0$，

$$\lambda\int_{G}u^2dxdy+\frac{1}{\lambda}\int_{G}\left(\frac{\partial^2 u}{\partial x^2}+\frac{\partial^2 u}{\partial y^2}\right)dxdy\geq2\int_{G}\left(\frac{\partial u}{\partial x}\right)^2+\left(\frac{\partial u}{\partial y}\right)^2dxdy$$

##### Solution 6
由于$u$在$\partial G$上恒为$0$，故由$Green Formula$有
    $$0=\int_{\partial G}u(u_xdy-u_ydx)=\iint_{G}(u_x^2+u_y^2+u\cdot u_{xx}+u\cdot u_{yy})dxdy\Rightarrow\iint_{G}(u_x^2+u_y^2)dxdy=\iint_{G}-u(u_{xx}+u_{yy})dxdy$$
    由$Cauchy-Schwart$积分不等式有：
    $$\begin{aligned}
    &\lambda\int_{G}u^2dxdy+\frac{1}{\lambda}\int_{G}\left(\frac{\partial^2 u}{\partial x^2}+\frac{\partial^2 u}{\partial y^2}\right)dxdy\geq2\iint_{G}\left|u(u_{xx}+u_{yy})\right|dxdy\\
    \geq&2\iint_{G}-u(u_{xx}+u_{yy})dxdy=2\iint_{G}(u_x^2+u_y^2)dxdy=2\int_{G}\left(\frac{\partial u}{\partial x}\right)^2+\left(\frac{\partial u}{\partial y}\right)^2dxdy
    \end{aligned}$$
    故综上：
    $$\lambda\int_{G}u^2dxdy+\frac{1}{\lambda}\int_{G}\left(\frac{\partial^2 u}{\partial x^2}+\frac{\partial^2 u}{\partial y^2}\right)dxdy\geq2\int_{G}\left(\frac{\partial u}{\partial x}\right)^2+\left(\frac{\partial u}{\partial y}\right)^2dxdy$$

## Solution for PDF
Click [Here](/files/Exam/Exam2024Fall-NKU-Analysis-Mid-Exam-Solution.pdf) and get the solution of this exam.
## Remark
If you have any questions or need further assistance, feel free to ask! Here is my email: [nkusherr1 at gmail.com](mailto:nkusherr1@gmail.com)
