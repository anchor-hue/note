> 姓名：甘缘
>
> 学号：202000820142

# Chapter 2

***Transforming Time Serie（变化时间序列）***



### note 1

> ***three general classes of transformations:***

- ***distributional（分布变换）***
- ***stationarity inducing（平稳性诱导变换）***
- ***decompositional（分解变换）***



## 1. Distributional Transformations（分布变换）



### note 2

> ***在 mean 和  variance 为  constant 的情况下，normally distributed, or at least are symmetric and not excessively kurtotic (fat-tailed) 通常表现地更好。***

> ***e.g. 序列只取 positive 或  nonnegative 的情况下，通常是右偏的（因为可以取到 infinite）。可以采取 logarithms 转化，通常以 e 为底。***

> ***转化成 logarithms 并不会导致 stationarity ，但是可以“straight out”趋势，使 variance 稳定。***

> ***the ratio of cumulative standard deviations(累计的标准差)：***

$$
\frac{s_i(x)}{s_i(log\ x)}
$$

> ***其中：***

$$
s^2_i(x) = i^{-1}\sum_{t=1}^i(x_t-\bar{x}_i)^2
$$

$$
\bar{x}_i = i^{-1}\sum_{t=1}^ix_t
$$

```
注：
当该比例在observation period中单调增加，那么可以认为，这对稳定standard deviation说有用的。
```



### note 3

> ***power transformations（包含 logarithmic, 对于 positive x, posed by Box and Cox）:***

$$
f^{BC}(x_t,\lambda) = 
\begin{cases}
\frac{(x_t^\lambda-1)}{\lambda} &\ \lambda \ne 0\\
logx_t &\ \lambda=0\\
\end{cases}
$$

> ***e.g. λ = 0.5(square root transformation)***

<img src="./images/figure2.4_1.png" style="zoom: 80%;" />



<img src="./images/figure2.4_2.png" style="zoom:80%;" />

```
注：变换之后，序列是symmetric，并且接近正态分布。
```



### note 4

> ***可以通过某些方式放松 Box-Cox transformation 中需要 positive values 的限制。***

> ***e.g. 对于 x 为 negative 但有下界的情况，可以采取 shift parameter（移位）。***

> ***替代方案：***

> ***signed power transformation( proposed by Bickel and Doksum):***

$$
f^{Sp}(x_t,\lambda) = \frac{(sgn(x_t)|x_t^{\lambda}|-1)}{\lambda}\ \ \ \lambda \gt0
$$

> ***generalized power (GP) transformation(suggested by Yeo and Johnson):***

$$
f^{GP}(x_t,\lambda) = 
\begin{cases}
\frac{((x_t+1)^{\lambda}-1)}{\lambda} &\ x_t\ge0,\lambda \ne0\\
log(x_t+1) &\ x_t\ge0,\lambda=0\\
\frac{-((-x_t+1)^{2-\lambda}-1)}{2-\lambda} &\ x_t\lt0,\lambda\ne2\\
-log(-x_t+1) &\ x_t\lt0,\lambda=2
\end{cases}
$$

> ***inverse hyperbolic sine (IHS，反双曲正弦) transformation(suggested by Burbidge):***

$$
f^{IHS}(x_t,\lambda) = \frac{sinh^{-1}(\lambda x_t)}{\lambda} = log\frac{\lambda x_t+(\lambda^2x_t^2+1)^{1/2}}{\lambda}\ \ \lambda\gt0
$$

```
注：parameter λ 可以通过 maximum likelihood 来估计。
```



### note 5

> ***假设有一个 transformation：***

$$
f(x_t,\lambda) = \mu_t+a_t
$$

> ***其中：***

$$
\mu_t
$$

> ***代表 mean***

$$
a_t
$$

> ***独立，服从 mean 为 0、variance 为 constant 的正态分布***



> ***利用  log-likelihood function 估计 λ：***

$$
l(\lambda)=C_f-(\frac{T}{2})\sum_{t=1}^Tlog\hat{a}_t^2+D_f(x_t,\lambda)
$$

> ***其中：***

$$
\hat{a}_t=f(x_t,\lambda)-\hat{\mu_t}
$$

> ***是 residuals（残差）***

$$
C_f
$$

> ***是 constant***

$$
D_f(x_t,\lambda)=
\begin{cases}
(\lambda-1)\sum_{t-1}^Tlog|x_T| &\ for\ BC\ and\ SP\\
(\lambda-1)\sum_{t=1}^Tsgn(x_t)log(|x_t|+1) &\ for\ GP\\
-\frac{1}{2}\sum_{t=1}^Tlog(1+\lambda^2x_t^2) &\ for\ IHS
\end{cases}
$$

> ***是根据具体的 transformation 进行具体的选择***


$$
2(l(\hat{\lambda})-l(\lambda))
$$

> ***的渐进分布为：***

$$
\chi^2(1)
$$

> ***可以据此找到 confidence interval***



## 2. Stationarity Inducing Transformations(平稳性诱导转换)



### note 6

> ***A simple stationarity transformation is to take successive（连续的） differences of a series***

### note 7

> ***first-difference of（一阶差分）:***

$$
\nabla x_t = x_t-x_{t-1}
$$

```
注：
当一阶差分不足够时，可以进行进一步的差分。
```

### note 8

> ***second-differences（ 二阶差分）:***

$$
\nabla\nabla x_t = \nabla^2x_t
$$

```
注：
二阶差分是 first-difference of the first-difference
```

> ***引入 lag operator（滞后算子） B：***

$$
B^jx_t \equiv x_{t-j}
$$

> ***因此，有：***

$$
\nabla x_t = x_t-x_{t-1} = x_t-Bx_t = (1-B)x_t
$$

$$
\nabla^2x_t = (1-B)^2x_t = (1-2B+B^2)x_t = x_t-2x_{t-1}+x_{t-2}
$$



> ***区别于 two-period difference：***

$$
x_t-x_{t-2} =  \nabla_2x_t
$$

> ***其中 j-period difference 是：***

$$
\nabla_j = 1-B^j
$$

### note 9

> ***proportional or percentage changes:***

$$
\frac{\nabla x_t}{x_{t-1}}\ \ or\ \ 100\frac{\nabla x_t}{x_{t-1}}
$$

```
注：
对于金融时间序列来说，这些通常被称为return。
如果是 percentage change in a price index，那么这些 changes 通常被称作 rate of inflation（通货膨胀率）。
```

### note 10

> ***relationship between the rate of change of a variable and its logarithm:***

> ***因为在 y趋于 0 时，有：***

$$
\log (1+y) \approx y
$$

> ***所以：***

$$
\frac{x_t-x_{t-1}}{x_{t-1}}=\frac{x_t}{x_{t-1}}-1\approx\log \frac{x_t}{x_{t-1}}=\log x_t-\log x_{t-1}=\nabla \log x_t
$$



## 3. Decomposing a Time Series and Smoothing Transformations(时间序列的分解与平滑转换)



### note 11

> ***decomposition form:***

$$
data = fit+residual
$$

> ***可能会产生 smooth series，有 form：***

$$
data = smooth+rough
$$

```
注：
可以通过running or moving medians来达到。
moving averages（MAs）是最受欢迎的smoothing时间序列的方法。
```



### note 12

> ***最简单的一种 MA：***

$$
MA(3)=\frac{1}{3}(x_{t-1}+x_t+x_{t+1})
$$

> ***更复杂的 (2n+1)-term weighted and centered（加权居中） MA：***

$$
WMA_t(2n+1)=\sum_{i=-n}^n\omega_ix_{t-i}
$$

> ***且满足约束：***

$$
\sum_{i=-n}^n\omega_i=1
$$

```
注：
weights通常是关于w0中心对称的。
```

```
注：
随着MA中包含的项越多，它就变得越平滑。
但是，由于在样本的开始和结束有n个观测值被“丢失”，n越大，失去的观测值就越多。
```



> ***uncentered MA:***

$$
\sum_{i=0}^n\omega_ix_{t-i}
$$

```
注：
只关注current和past的observations。
```



> ***a simple MA with an even number of terms:***

> ***e.g.  a four-term MA:***

$$
MA_{t-1/2}(4)=\frac{1}{4}(X_{t-2}+x_{t-1}+x_t+x_{t+1})
$$

$$
MA_{t+1/2}(4)=\frac{1}{4}(x_{t-1}+x_t+x_{t+1}+X_{t+2})
$$

> ***Taking the average of these two simple MAs :***

$$
WMA_t(5)=\frac{1}{8}x_{t-2}+\frac{1}{4}x_{t-1}+\frac{1}{4}x_t+\frac{1}{4}x_{t+1}+\frac{1}{8}x_{t+2}
$$



```
注：、
MA的权重取决于smoothing parameter。
选择较大的值是为了产生相对“平稳的趋势”。
```



### note 13

> ***When a time series is observed at a frequency greater than annual, a three-component decomposition is often warranted:***

> ***additive decomposition:***

$$
X_t=T_t+S_t+I_t
$$

> ***multiplicative decomposition:***

$$
X_t=T_t\times S_t\times I_t
$$

```
注：
denoted Xt, being decomposed into trend, Tt, seasonal, St, and irregular, It, components.

可以将multiplicative的通过取logarithms得到additive的。

seasonal component : a regular, short-term, annual cycle
irregular component : random and unpredictable
```



> ***seasonally adjusted series:***

$$
X_t^{SA,A}=X_t-S_t=T_t+I_t
$$

$$
X_t^{SA,M}=\frac{X_t}{S_t}=T_t\times I_t
$$



## summary

$$
1.如果x_t是由\ exponential\ trend\ x_t=Ae^{\beta t}生成的，那么\log{x_t}=\log{A}+\beta t是\ linear\ trend。
$$

$$
因此，\beta=d\log{x_t}/dt=(dx_t/dt)/x_t是x的变化率。
$$

$$
2.当方差与级数的水平成正比时，建议采用平方根变换 。
$$

$$
3.因素的总和必须为零，所以如果原始的计算结果不为零，那么就需要进行调整。
$$

$$
e.g.如果这个总和是a\neq0，那么每个因素就应该减去a/4。
$$

