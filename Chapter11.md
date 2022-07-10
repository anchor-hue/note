> 姓名：甘缘
>
> 学号：202000820142

# Chapter 11

***Nonlinear Stochastic Processes(非线性随机过程)***



## MARTINGALES, RANDOM WALKS, AND NONLINEARITY(鞅，随机游动和非线性)

### note 1

> ***A martingale:***

$$
E\left(\left|x_{t}\right|\right)<\infty\  for\  each \ t
$$

$$
E\left(x_{t} \mid x_{s}, x_{s-1}, \ldots\right)=x_{s}
$$

Written as

$$
E\left(x_{t}-x_{s} \mid x_{s}, x_{s-1}, \ldots\right)=0, \quad s<t,
$$

推广到以下情况:
$$
E\left(x_{t}-x_{s} \mid x_{s}, x_{s-1}, \ldots\right) \geq 0, \quad s<t,
$$
written equivalently as:

$$
x_{t}=x_{t-1}+a_{t},
$$

### note 2

Romano and Thombs show:
$$
\begin{gathered}
\operatorname{Cov}\left(w_{1} w_{2}, w_{i+1} w_{i+2}\right)=0 \\
V\left(w_{1} w_{2}\right)=E\left(w_{1}^{2} w_{2}^{2}\right)=\left(E\left(z_{0}^{2}\right)\right)^{2} E\left(z_{1}^{4}\right)=\sigma_{z}^{4} E\left(z_{1}^{4}\right)
\end{gathered}
$$

and

$$
\sigma_{w}^{2}=E\left(w_{t}^{2}\right)=E\left(z_{t}^{2} z_{t-1}^{2}\right)=\sigma_{z}^{4}
$$

Thus

$$
\tau^{2}=\frac{E\left(z_{1}^{4}\right)}{\sigma_{z}^{4}}>1
$$

### note 3

> ***modifying the portmanteau statistic to:***

$$
\tilde{Q}(K)=T \sum_{i=1}^{K}\left(\frac{r_{i}^{2}}{v_{i}}\right) \stackrel{a}{\sim} \chi_{K}^{2}
$$

其中

$$
v_{i}=T^{-1} \sum_{t=i+1}^{T} \frac{\left(w_{t}-\bar{w}\right)^{2}\left(w_{t-i}-\bar{w}\right)^{2}}{\hat{\sigma}_{w}^{4}}
$$



## NONLINEAR STOCHASTIC MODELS(非线性随机模型)

### note 4

```
如果一个随机过程不满足分解的假设，那么它可以被认为是非线性的。
```

for example:
$$
x_{t}-\mu=f\left(a_{t}, a_{t-1}, a_{t-2}, \ldots\right)
$$
 Taylor expansion 在0处：
$$
x_{t}-\mu=f\left(0, a_{t-1}, a_{t-2}\right)+a_{t} f^{\prime}\left(0, a_{t-1}, a_{t-2}\right)+0.5 a_{t}^{2} f^{\prime \prime}\left(0, a_{t-1}, a_{t-2}\right)+\cdots
$$

> ***Wecker(1981)引入了非对称移动平均过程，其一阶形式为:***

$$
x_{t}=a_{t}+\theta a_{t-1}+\psi \mathbf{1}\left(a_{t-1}>0\right) a_{t-1}
$$



## BILINEAR MODELS(双线性时间序列模型)

### note 5

> ***bilinear model:***

$$
\phi(B)\left(x_{t}-\mu\right)=\theta(B) \varepsilon_{t}+\sum_{i=1}^{R} \sum_{j=1}^{S} \gamma_{i j} x_{t-i} \varepsilon_{t-j}
$$

> ***characterized as:***

$$
x_{t}=\varepsilon_{t}+\gamma_{i j} x_{t-i} \varepsilon_{t-j}
$$

For example:
$$
x_{t}=\left(a+b \varepsilon_{t-1}\right) x_{t-1}+\varepsilon_{t}
$$
first differences as:

$$
\nabla x_{t}=b x_{t-1} \varepsilon_{t-1}+\varepsilon_{t}
$$

a = 1:
$$
x_{t}=\varphi_{t} x_{t-1}+\varepsilon_{t}
$$
assume:
$$
\nabla x_{t} \approx \varepsilon_{t}
$$
formulated as:

$$
\nabla x_{t}=b x_{t-1} \nabla x_{t-1}+u_{t}
$$

### note 6

Suppose the true model for x_{t}  but the ARMA model

$$
\tilde{\phi}(B)\left(x_{t}-\tilde{\mu}\right)=\tilde{\theta}(B) \tilde{\varepsilon}_{t}
$$

is fitted.

residual:
$$
\tilde{\varepsilon}_{t}=\vartheta_{1}(B) \varepsilon_{t}+\vartheta_{2}(B) \sum_{i=1}^{R} \sum_{j=1}^{S} \gamma_{i j} x_{t-i} \varepsilon_{t-j}
$$

### note 7

双线性的另一种形式:
$$
\phi(B)\left(x_{t}-\mu\right)=\theta(B) a_{t}
$$

$$
a_{t}=\varepsilon_{t}+\sum_{i=1}^{R} \sum_{j=1}^{S} \gamma_{i j} a_{t-i} \varepsilon_{t-j}
$$



## THRESHOLD AND SMOOTH TRANSITION AUTOREGRESSIONS(阈值和平滑过渡自回归)

### note 8

```
一种流行的非线性模型是自激阈值自回归(SETAR)过程，它通过定义一组开关点或“阈值”通常未知的分段自回归模型来允许不对称。
```

$$
x_{t}=\sum_{j=1}^{r}\left(\phi_{j, 1} x_{t-1}+\cdots+\phi_{j, p} x_{t-p}+a_{j, t}\right) \mathbf{1}\left(c_{j-1}<x_{t-d} \leq c_{j}\right)
$$

### note 9

```
SETAR的提法要求从一种制度到另一种制度的转变是立即的。
```

> ***通过定义指数自回归(EAR)过程来实现位移平滑:***

$$
x_{t}=\phi_{1} x_{t-1}+\cdots+\phi_{p} x_{t-p}+G\left(\gamma, x_{t-d}\right)\left(\varphi_{1} x_{t-1}+\cdots+\varphi_{p} x_{t-p}\right)+a_{t}
$$

其中 the transition function:
$$
G\left(\gamma, x_{t-d}\right)=\exp \left(-\gamma x_{t-d}^{2}\right), \quad \gamma>0
$$
加入位置参数c来考虑过渡函数中的不对称性:
$$
G_{E}\left(\gamma, c, x_{t-d}\right)=\exp \left(-\gamma\left(x_{t-d}-c\right)^{2}\right), \quad \gamma>0
$$

> ***logistic STAR(LSTAR)模型:***

$$
G_{L}\left(\gamma, c, x_{t-d}\right)=\left(1+\exp \left(-\gamma\left(x_{t-d}-c\right)\right)\right)^{-1}, \quad \gamma>0
$$

```
注：
ESTAR和LSTAR模型都可以用非线性最小二乘(NLS)和ML技术估计，尽管其性质
ML估计量通常是未知的。然而，当跃迁参数γ较大时，可能会出现数值问题，因为此时跃迁是快速和准确的，该参数的估计需要许多观测位于位置参数c的一个小邻域内。
```



## MARKOV-SWITCHING MODELS(马尔可夫转换模型)

### note 10

> *** two-state Markov process:***

$$
z_{t}=\alpha_{0}+\alpha_{1} S_{t}
$$

其中
$$
\begin{gathered}
P\left(S_{t}=1 \mid S_{t-1}=1\right)=p \\
P\left(S_{t}=0 \mid S_{t-1}=1\right)=1-p \\
P\left(S_{t}=1 \mid S_{t-1}=0\right)=1-q \\
P\left(S_{t}=0 \mid S_{t-1}=0\right)=q
\end{gathered}
$$

### note 11

St的随机过程是严格平稳的，有AR(1)表示:
$$
S_{t}=(1-q)+\lambda S_{t-1}+V_{t}
$$
其中
$$
\lambda=p+q-1
$$

$$
\begin{aligned}
&P\left(V_{t}=(1-p) \mid S_{t-1}=1\right)=p, \\
&P\left(V_{t}=-p \mid S_{t-1}=1\right)=1-p, \\
&P\left(V_{t}=-(1-q) \mid S_{t-1}=0\right)=q, \\
&P\left(V_{t}=q \mid S_{t-1}=0\right)=1-q
\end{aligned}
$$

### note 12

模型的ML估计将噪声分量写为:
$$
u_{t}=x_{t}-\alpha_{0}-\alpha_{1} S_{t}
$$

$$
the \ innovations\  \varepsilon_{t}=\phi(B) u_{t}:
$$

$$
\varepsilon_{t}=\phi(B)\left(x_{t}-\alpha_{0}-\alpha_{1} S_{t}\right)
$$

```
注：
该表达式可以用来计算对数似然函数，注意到它可以分解为条件(在过去的观察中)对数似然的和。
```



## NEURAL NETWORKS(神经网络)

### note 13

```
神经网络(NNs)是一类广泛的非参数模型，近年来在广泛的学科中得到了广泛的普及，包括计算机科学、心理学、生物学、语言学和模式识别(例如，教科书中的处理方法，参见Haykin, 1999)。这些模型起源于认知科学中对模拟人脑结构和行为的研究。
```

```
这些模型被组织成三个基本层:自变量的输入层，因变量的输出层，以及中间的一个或多个隐藏层。
```

> *** A univariate autoregressive MLP model with a single hidden layer:***

$$
x_{t}=\sum_{i=1}^{p} \phi_{i} x_{t-i}+\sum_{j=1}^{q} \beta_{j} G\left(\sum_{i=1}^{p} \varphi_{i} x_{t-i}\right)+\varepsilon_{t}
$$

```
注：
MLPs的一个主要问题是它们的“黑箱”特性，因为模型的参数和结构提供的直觉很少，只能通过模拟或敏感性分析含蓄地得出结论。
```



## NONLINEAR DYNAMICS AND CHAOS(非线性动力学与混沌)

### note 14

```
广义地说，混沌是一个简单(低维)、非线性、动态系统产生复杂(无限维或类似随机)行为的数学条件。
```

 example of a chaotic process:
$$
x_{t}=f\left(x_{t-1}\right), \quad x_{0} \in[0,1]
$$

其中

![](https://cdn.mathpix.com/cropped/2022_06_30_e4f262c32958d9ffb3aag-096.jpg?height=66&width=408&top_left_y=661&top_left_x=235)

> ***logistic map：***

$$
x_{t}=4 x_{t-1}\left(1-x_{t-1}\right)=4 x_{t-1}-4 x_{t-1}^{2}, \quad 0<x_{0}<1
$$



## TESTING FOR NONLINEARITY(测试非线性)

### note 15

```
在时间序列建模之前经常应用的非线性转换，也可能诱发非线性行为。
季节性的调整可能会平滑结构的转变和政权之间的切换。
在所有情况下，没有非线性检验占主导地位，幂随样本大小和潜在随机过程的特征而变化。
```

### note 16

> ***Regression Error Specification Test (RESET):***

$$
e_{t}=\sum_{i=1}^{p} \varphi_{i} x_{t-i}+\sum_{j=2}^{h} \delta_{j} \hat{x}_{t}^{j}+v_{t}
$$

> *** auxiliary regression with second-order terms:***

$$
e_{t}=\sum_{i=1}^{p} \varphi_{i} x_{t-i}+\sum_{i=1}^{p} \sum_{j=i}^{p} \delta_{i j} x_{t-i} x_{t-j}+v
$$

> ***A further extension:***

$$
e_{t}=\sum_{i=1}^{p} \varphi_{i} x_{t-i}+\sum_{i=1}^{p} \sum_{j=i}^{p} \delta_{i j} x_{t-i} x_{t-j}+\sum_{i=1}^{p} \sum_{j=i}^{p} \sum_{k=j}^{p} \delta_{i j k} x_{t-i} x_{t-j} x_{t-k}+v_{t}
$$



### note 17

> ***an ARCH-type model:***

$$
e_{t}=g\left(x_{t-1}, \ldots, x_{t-k}, e_{t-1}, \ldots, e_{t-k}\right) u_{t}
$$

multiplicative dependence implies that:
$$
E\left(e_{t} \mid x_{t-1}, \ldots, x_{t-k}, e_{t-1}, \ldots, e_{t-k}\right)=0
$$
 estimating the scaled third moment of the data:
$$
r_{e e e}(i, j)=\frac{T^{-1} \sum e_{t} e_{t-i} e_{t-j}}{\left(T^{-1} \sum e_{t}^{2}\right)^{1.5}}
$$
variance:
$$
\sigma^{2}=\frac{T^{-1} \sum e_{t}^{2} e_{t-i}^{2} e_{t-j}^{2}}{\left(T^{-1} \sum e_{t}^{2}\right)^{3}}
$$

### note 18

> *** TR test statistic, estimated for various lags k as:***

$$
T R(k)=\hat{B}_{2,1}(k)-\hat{B}_{1,2}(k)
$$

其中
$$
\hat{B}_{i, j}(k)=(T-k)^{-1} \sum_{t=k+1}^{T} e_{t}^{i} e_{t-k}^{j} \quad i, j=1,2
$$
且
$$
V(T R(k))=2 \frac{\left(\mu_{4} \mu_{2}-\mu_{3}\right)}{T-k}-2 \frac{\mu_{2}^{3}(T-2 k)}{(T-k)^{2}}, \quad \mu_{i}=E\left(e_{t}^{i}\right) .
$$

### note 19

> ***correlation integral:***

$$
C_{N}(\ell, T)=\frac{2}{T_{N}\left(T_{N}-1\right)} \sum_{t<s} \mathrm{I}_{t}\left(x_{t}^{N}, x_{s}^{N}\right)
$$

其中e
$$
x_{t}^{N}=\left(x_{t}, x_{t+1}, \ldots, x_{t+N-1}\right)
$$

and

$$
x_{s}^{N}=\left(x_{s}, x_{s+1}, \ldots, x_{s+N-1}\right)
$$

if the x_{t}s are strict white noise

$$
C_{N}(\ell, T) \rightarrow C_{1}(\ell, T)^{N}, \text { as } T \rightarrow \infty
$$

and

$$
w_{N}(\ell, T)=\frac{\sqrt{T}\left(C_{N}(\ell, T)-C_{1}(\ell, T)^{N}\right)}{\sigma_{N}(\ell, T)}
$$

 ## FORECASTING WITH NONLINEAR MODELS(非线性模型预测)

### note 20

> *** two-step ahead forecast:***

$$
f_{T, 2}=E\left(x_{T+2} \mid x_{T}\right)=E\left(g\left(g\left(x_{T+1}\right)+\varepsilon_{T+1}\right)\right)=\int_{\varepsilon} g\left(g\left(x_{T+1}\right)+\varepsilon_{T+1}\right) d F(\varepsilon)
$$

```
可以通过模拟或自举拟合模型的残差来逼近。
```

