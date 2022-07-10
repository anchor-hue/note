> 姓名：甘缘
>
> 学号：202000820142

# Chapter 16

***Compositional and Count Time Series***

## CONSTRAINED TIME SERIES(限制时间序列)

### note 1

```
有些级数，或级数组，会受到进一步的约束。当建模这样的系列时，“好的”模型应该不能预测违反已知约束的值，即该模型应该是“预测连贯”的。
```



## MODELING COMPOSITIONAL DATA(建模的数据)

### note 2

written in matrix form as

$$
\boldsymbol{X}=\left[\begin{array}{cccc}
x_{1,1} & x_{1,2} & \cdots & x_{1, D} \\
x_{2,1} & x_{2,2} & \cdots & x_{2, D} \\
\vdots & \vdots & & \vdots \\
x_{T, 1} & x_{T, 2} & \cdots & x_{T, D}
\end{array}\right]=\left[\begin{array}{llll}
\boldsymbol{x}_{1} & \boldsymbol{x}_{2} & \cdots & \boldsymbol{x}_{D}
\end{array}\right]
$$

The sub-matrix

$$
\boldsymbol{X}^{(d)}=\left[\begin{array}{llll}
\boldsymbol{x}_{1} & \boldsymbol{x}_{2} & \cdots & \boldsymbol{x}_{d}
\end{array}\right]
$$

embedded in D-dimensional real space with

$$
\boldsymbol{x}_{D}=\iota-\sum_{i=1}^{d} \boldsymbol{x}_{i}
$$

### note 3

> ***the additive log-ratio transformation:***

$$
\begin{aligned}
\boldsymbol{Y} &=\left[\begin{array}{llll}
\boldsymbol{y}_{1} & \boldsymbol{y}_{2} & \cdots & \boldsymbol{y}_{d}
\end{array}\right]=a_{d}\left(\boldsymbol{X}^{(d)}\right) \\
&=\left[\begin{array}{llll}
\log \left(\frac{\boldsymbol{x}_{1}}{\boldsymbol{x}_{D}}\right) & \log \left(\frac{\boldsymbol{x}_{2}}{\boldsymbol{x}_{D}}\right) & \cdots & \log \left(\frac{\boldsymbol{x}_{d}}{\boldsymbol{x}_{D}}\right)
\end{array}\right]
\end{aligned}
$$

> *** the additive-logistic:***

$$
\begin{gathered}
\boldsymbol{X}^{(d)}=a_{d}^{-1}(\boldsymbol{Y})=\left[\begin{array}{ccc}
\frac{\exp \left(\boldsymbol{y}_{1}\right)}{\boldsymbol{y}} & \frac{\exp \left(\boldsymbol{y}_{2}\right)}{\boldsymbol{y}} \quad \cdots & \frac{\exp \left(\boldsymbol{y}_{d}\right)}{\boldsymbol{y}}
\end{array}\right] \\
\boldsymbol{x}_{D}=\frac{1}{\boldsymbol{y}}
\end{gathered}
$$

其中
$$
\boldsymbol{y}=1+\sum_{i=1}^{d} \exp \left(\boldsymbol{y}_{i}\right)
$$
X will have a logistic-normal distribution:
$$
\boldsymbol{X}^{(d)} \sim L^{d}(\boldsymbol{\mu}, \boldsymbol{\Sigma})=2 \pi^{-d / 2}|\boldsymbol{\Sigma}|^{-1 / 2}\left(\prod_{i=1}^{D} \boldsymbol{x}_{i}\right)^{-1} \exp \left(-\frac{1}{2}(\boldsymbol{Y}-\boldsymbol{\mu})^{\prime} \boldsymbol{\Sigma}^{-1}(\boldsymbol{Y}-\boldsymbol{\mu})\right)
$$

### note 4

> ***centered log-ratio transformation:***



$$
\boldsymbol{Z}=c_{d}\left(\boldsymbol{X}^{(d)}\right)=\left[\log \left(\frac{\boldsymbol{x}_{1}}{g(\boldsymbol{X})}\right) \quad \log \left(\frac{\boldsymbol{x}_{2}}{g(\boldsymbol{X})}\right) \quad \cdots \quad \log \left(\frac{\boldsymbol{x}_{D}}{g(\boldsymbol{X})}\right)\right]
$$

其中

$$
g(\boldsymbol{X})=\left[\begin{array}{c}
\left(x_{1,1} \times x_{1,2} \times \cdots \times x_{1, D}\right)^{1 / D} \\
\left(x_{2,1} \times x_{2,2} \times \cdots \times x_{2, D}\right)^{1 / D} \\
\vdots \\
\left(x_{T, 1} \times x_{T, 2} \times \cdots \times x_{T, D}\right)^{1 / D}
\end{array}\right]
$$



## FORECASTING COMPOSITIONAL TIME SERIES(预测成分时间序列)

### note 5

> ***A forecast for Xt+h:***

$$
\boldsymbol{X}_{t}(h)=a_{d}^{-1}\left(\boldsymbol{Y}_{t}(h)\right)
$$

Under the normality assumption for Yt, a 100(1- α)% confidence region for Xt+h can be formed from:
$$
\left(\boldsymbol{Y}_{t}(h)-\log \left(\frac{\boldsymbol{X}_{t+h}^{(d)}}{\boldsymbol{X}_{D, t+h}}\right)\right)^{\prime} \boldsymbol{\Sigma}_{t}^{-1}(h)\left(\boldsymbol{Y}_{t}(h)-\log \left(\frac{\boldsymbol{X}_{t+h}^{(d)}}{\boldsymbol{X}_{D, t+h}}\right)\right) \leq \chi_{\alpha}^{2}(d)
$$


## TIME SERIES MODELS FOR COUNTS: THE IN-AR(1) BENCHMARK MODEL(计数的时间序列模型:IN-AR (1)基准模型)

### note 6

```
整数值ARMA(IN-ARMA)模型提供了一类有趣的离散值过程，不仅能够指定一系列计数的依赖结构，而且能够在广泛的(离散的)边际分布之间做出选择。
```

> ***“benchmark” IN-AR(1) process:***

$$
x_{t}=a \circ x_{t-1}+w_{t}
$$

> ***binomial thinning operation:***

$$
a \circ x_{t-1}=\sum_{i=1}^{x_{t-1}} y_{i, t-1}
$$

y_{i,t-1}是Bernoulli随机变量
$$
P\left(y_{i, t-1}=1\right)=a
$$

and

$$
P\left(y_{i, t-1}=0\right)=1-a
$$

### note 7

The unconditional moments of x_{t} are

$$
E\left(x_{t}\right)=\frac{\mu_{w}}{(1-a)}
$$

and

$$
V\left(x_{t}\right)=\frac{\left(a \mu_{w}+\sigma_{w}^{2}\right)}{\left(1-a^{2}\right)}
$$

且有

$$
E\left(x_{t} \mid x_{t-1}\right)=a x_{t-1}+\mu_{w}
$$

and

$$
V\left(x_{t} \mid x_{t-1}\right)=a(1-a) x_{t-1}+\sigma_{w}^{2}
$$



## OTHER INTEGER-VALUED ARMA PROCESSES(其他整数值ARMA过程)

### note 8

> ***IN-MA(1) process:***

$$
x_{t}=w_{t}+b \circ w_{t-1}
$$

$$
b \circ w_{t-1}=\sum_{i=1}^{w_{t-1}} y_{i, t-1}
$$

> ***The autocorrelation function (ACF) of xt:***

$$
\rho_{k}=\left\{\begin{array}{ccc}
\frac{b \sigma_{w}^{2}}{b(1-b) \mu_{w}+\left(1+b^{2}\right) \sigma_{w}^{2}} & \text { for } & k=1 \\
0 & \text { for } & k>1
\end{array}\right.
$$

### note 9

> ***IN-AR(2) process:***

$$
x_{t}=a_{1} \circ x_{t-1}+a_{2} \circ x_{t-2}+w_{t}
$$

ACF满足二阶差分方程：
$$
\rho_{k}=a_{1} \rho_{k-1}+a_{2} \rho_{k-2}
$$


## ESTIMATION OF INTEGER-VALUED ARMA MODELS(整值ARMA模型的估计)

### note 10

> ***“bias-corrected Yule-Walker” estimate:*** 

$$
\hat{a}=\frac{1}{T-3}\left(T r_{1}+1\right)
$$

 estimate of λ:
$$
\hat{\lambda}=(1-\hat{a}) \bar{x}
$$
Po-IN-AR(2)模型中a1和a2的Yule-Walker估计:
$$
\hat{a}_{1}=\frac{r_{1}\left(1-r_{2}\right)}{1-r_{1}^{2}} \quad \hat{a}_{2}=\frac{r_{2}-r_{1}^{2}}{1-r_{1}^{2}}
$$
estimate of λ:
$$
\hat{\lambda}_{2}=\left(1-\hat{a}_{1}-\hat{a}_{2}\right) \bar{x}
$$


## TESTING FOR SERIAL DEPENDENCE IN COUNT TIME SERIES(count时间序列中序列相关性的检验)

### note 11

other two tests:
$$
Q_{\mathrm{acf}}(1)=\frac{\hat{r}_{2}^{2}\left(\sum_{t=1}^{T}\left(x_{t}-\bar{x}\right)^{2}\right)^{2}}{\sum_{t=3}^{T}\left(x_{t}-\bar{x}\right)^{2}\left(x_{t-2}-\bar{x}\right)^{2}}
$$

and

$$
Q_{\text {pacf }}(1)=\frac{\hat{\phi}_{2}^{2}\left(\sum_{t=1}^{T}\left(x_{t}-\bar{x}\right)^{2}\right)^{2}}{\sum_{t=3}^{T}\left(x_{t}-\bar{x}\right)^{2}\left(x_{t-2}-\bar{x}\right)^{2}}
$$

```
注：
如果这三个统计数据都不显著，那么xt可能没有依赖结构。
```



### FORECASTING COUNTS(预测数量)

### note 12

> ***Forecasting with Univariate Models:***

$$
f_{T, h}=E\left(x_{T+h} \mid x_{T}, x_{T-1}, \ldots, x_{1}\right)
$$

且有:
$$
\begin{gathered}
f_{T, 1}=a x_{T}+\mu_{w} \\
f_{T, 2}=a f_{T, 1}+\mu_{w}=a^{2} x_{T}+(1+a) \mu_{w}
\end{gathered}
$$

and

$$
f_{T, h}=a^{h} x_{T}+\left(1+a+a^{2}+\cdots+a^{h-1}\right) \mu_{w}
$$

```
注：
中位数具有最小化预期绝对预测误差的最优性，建议计算整个h步超前(条件)预测分布。
```

在泊松创新假设下，IN-AR(1)模型:



$$
p_{h}\left(x \mid x_{T}\right)=x_{T} ! \exp \left(-\lambda\left(\frac{\left(1-a^{h}\right)}{(1-a)}\right)\right) C_{h}\left(x_{T}, x\right) \quad x=0,1,2, \ldots
$$

其中

$$
C_{h}\left(x_{T}, x\right)=\sum_{k=0}^{m} \frac{a^{k h}\left(1-a^{h}\right)^{x_{T}-k} \lambda^{x-k}}{k !(x-k) !\left(\left|x_{T}-k\right|\right) !} \quad m=\min \left(x_{T}, x\right)
$$



## INTERMITTENT AND NONNEGATIVE TIME SERIES(间歇非负时间序列)

### note 13

```
当一个计数序列包含许多0时，它有时被称为是间歇性的，就像库存只是偶尔需要。
隐含模型与间歇性需求数据的属性不一致，因为它们必须是非平稳的。
```

