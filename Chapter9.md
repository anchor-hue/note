> 姓名：甘缘
>
> 学号：202000820142

# Chapter 9

***Seasonality and Exponential Smoothing(季节性和指数平滑)***



## SEASONAL PATTERNS IN TIME SERIES(时间序列中的季节模式)

### note 1

```
季节性的存在常常从系列的情节中立即显现出来，但它也会表现为适当差异数据的样本自相关函数(SACF)。
季节模式是这些系列的一个可预测特征,它容易受到明确建模或被适当的季节调整程序移除的影响。
```



## MODELING DETERMINISTIC SEASONALITY(建模确定的季节性)

### note 2

> ***“seasonal mean” model:***

$$
x_{t}=\sum_{i=1}^{m} \alpha_{i} s_{i, t}+\varepsilon_{t}
$$



## MODELING STOCHASTIC SEASONALITY(随机建模的季节性)

### note 3

```
季节性自相关性的缓慢下降表明了季节性的非平稳性，类似于“非季节性非平稳性”的分析，可以通过季节差分来处理。
```

> ***a seasonal ARIMA model：***

$$
\nabla^{d} \nabla_{m}^{D} \phi(B) x_{t}=\theta(B) a_{t}
$$

自相关性可以用第二个非季节性过程来建模:
$$
\phi(B) \nabla^{d} \alpha_{t}=\theta(B) a_{t}
$$

> ***the general multiplicative seasonal model:：***

$$
\phi_{p}(B) \Phi_{P}\left(B^{m}\right) \nabla^{d} \nabla_{m}^{D} x_{t}=\theta_{q}(B) \Theta_{Q}\left(B^{m}\right) a_{t}
$$

```
注：
一般的乘法模型较为复杂，其ACF和PACF的显式表达式难以提供。
```



### note 4

> *** the multiplicative ARIMA(0,1,1) (0,1,1)m model:：***

$$
\nabla \nabla_{m} x_{t}=(1-\theta B)\left(1-\Theta B^{m}\right) \alpha_{t}
$$

written as:

$$
w_{t}=\left(1-B-B^{m}+B^{m+1}\right) x_{t}=\left(1-\theta B-\Theta B^{m}+\theta \Phi B^{m+1}\right) a_{t}
$$

the autocovariances of w_{t}:

$$
\begin{aligned}
\gamma_{k}=& E\left(w_{t} w_{t-k}\right) \\
=& E\left(a_{t}-\theta a_{t-1}-\Theta a_{t-m}+\theta \Theta a_{t-m-1}\right) \\
& \times\left(a_{t-k}-\theta a_{t-1-k}-\Theta a_{t-m-k}+\theta \Theta a_{t-m-1-k}\right)
\end{aligned}
$$

these being

$$
\begin{aligned}
\gamma_{0} &=\left(1+\theta^{2}\right)\left(1+\Theta^{2}\right) \sigma^{2} \\
\gamma_{1} &=-\theta\left(1+\Theta^{2}\right) \sigma^{2} \\
\gamma_{m-1} &=\theta \Theta \sigma^{2} \\
\gamma_{m} &=-\Theta\left(1+\theta^{2}\right) \sigma^{2} \\
\gamma_{m+1} &=\theta \Theta \sigma^{2}
\end{aligned}
$$

> *** the ACF is:***

$$
\begin{aligned}
\rho_{1} &=-\frac{\theta}{1+\theta^{2}} \\
\rho_{m-1} &=\frac{\theta \Theta}{\left(1+\theta^{2}\right)\left(1+\Theta^{2}\right)} \\
\rho_{m} &=-\frac{\Theta}{1+\Theta^{2}} \\
\rho_{m+1} &=\rho_{m-1}=\rho_{1} \rho_{m}
\end{aligned}
$$

### note 5

滞后大于m+1时估计的样本自相关方差为:
$$
V\left(r_{k}\right)=T^{-1}\left(1+2\left(r_{1}^{2}+r_{m-1}^{2}+r_{m}^{2}+r_{m+1}^{2}\right)\right) \quad k>m+1
$$


## MIXED SEASONAL MODELS(混合季节性模型)

### note 6

> ***normal settings:***

$$
x_{t}=\sum_{i=1}^{m} \alpha_{i} s_{i, t}+\frac{\theta_{q}(B) \Theta_{Q}\left(B^{m}\right)}{\phi_{p}(B) \Phi_{P}\left(B^{m}\right) \nabla \nabla_{m}} a_{t}
$$



## SEASONAL ADJUSTMENT(季节性调整)

### note 7

> ***implicit UC decomposition:***

$$
x_{t}=z_{t}+s_{t}+u_{t}
$$

```
注：
进行季节性调整是为了简化数据，以便能够更容易地解释这些数据，而不会因为这种简化而造成太大的信息损失。
```



## EXPONENTIAL SMOOTHING(指数平滑法)

### note 8

xt当前和过去观测值的指数加权移动平均值:
$$
\begin{aligned}
z_{t} &=\alpha x_{t}+\alpha(1-\alpha) x_{t-1}+\alpha(1-\alpha)^{2} x_{t-2}+\cdots=\alpha \sum_{j=0}^{\infty}(1-\alpha)^{j} x_{t-j} \\
&=\alpha\left(1+(1-\alpha) B+(1-\alpha)^{2} B^{2}+\cdots+(1-\alpha)^{j} B^{j}+\cdots\right) x_{t}
\end{aligned}
$$
written as:

$$
(1-(1-\alpha) B) z_{t}=\alpha x_{t}
$$

or

$$
z_{t}=\alpha x_{t}+(1-\alpha) z_{t-1}
$$

“error correction” form:
$$
z_{t}=z_{t-1}+\alpha\left(x_{t}-z_{t-1}\right)=z_{t-1}+\alpha e_{t}
$$


### note 9

```
注：
对于没有趋势的序列，简单指数平滑是一种合适的预测方法。
```

> ***趋势分量：***

$$
\begin{aligned}
z_{t} &=\alpha x_{t}+(1-\alpha)\left(z_{t-1}+\tau_{t-1}\right) \\
&=z_{t-1}+\tau_{t-1}+\alpha e_{t}
\end{aligned}
$$

> ***updating equation for the trend τ_t:***

$$
\begin{aligned}
\tau_{t} &=\beta\left(z_{t}-z_{t-1}\right)+(1-\beta) \tau_{t-1} \\
&=\tau_{t-1}+\alpha \beta e_{t}
\end{aligned}
$$

> ***Forecasts:***

$$
f_{T, h}=z_{T}+\tau_{T} h
$$

Holt-Winters model is equivalent to the ARIMA(0,2,2)  process:
$$
\nabla^{2} x_{t}=\left(1-(2-\alpha-\alpha \beta) B-(\beta-1) B^{2}\right) a_{t}
$$
general process:
$$
\nabla^{2} x_{t}=\left(1-\theta_{1} B-\theta_{2}\right) a_{t}
$$
the smoothing parameters:
$$
\alpha=1+\theta_{2}
$$
and
$$
\beta=\left(1-\theta_{1}-\theta_{2}\right) /\left(1+\theta_{2}\right)
$$


### note 10

> ***double exponential smoothing:***

$$
\begin{aligned}
&z_{t}=\gamma x_{t}+(1-\gamma) z_{t-1} \\
&\tau_{t}=\gamma\left(z_{t}-z_{t-1}\right)+(1-\gamma) \tau_{t-1}
\end{aligned}
$$

Double exponential smoothing is equivalent to the restricted ARIMA(0,2,2) process:
$$
\nabla^{2} x_{t}=(1-(1-\gamma) B)^{2} a_{t}=\left(1-2(1-\gamma) B+(1-\gamma)^{2} B^{2}\right) a_{t}
$$


### note 11

updating equation:

$$
\begin{aligned}
z_{t}=& \alpha\left(x_{t}-s_{t-m}\right)+(1-\alpha)\left(z_{t-1}+\tau_{t-1}\right)=z_{t-1}+\tau_{t-1} \\
&+\alpha\left(x_{t}-s_{t-m}-z_{t-1}-\tau_{t-1}\right)=z_{t-1}+\tau_{t-1}+\alpha e_{t}
\end{aligned}
$$

 an additional seasonal updating equation:

$$
s_{t}=\delta\left(x_{t}-z_{t}\right)+(1-\delta) s_{t-m}=s_{t-m}+\delta(1-\beta) e_{t}
$$

Forecasts:

$$
f_{T, h}=z_{T}+\tau_{T}+s_{T+h-m}
$$

equivalent to the ARIMA model:
$$
\nabla \nabla_{m} x_{t}=\theta_{m+1}(B) a_{t}
$$

其中

$$
\begin{aligned}
\theta_{1} &=1-\alpha-\alpha \beta \\
\theta_{2} &=\cdots=\theta_{m-1}=-\alpha \beta \\
\theta_{m} &=1-\alpha \beta-(1-\alpha) \delta \\
\theta_{m+1} &=-(1-\alpha)(1-\delta)
\end{aligned}
$$



### note 12

```
在建模季节时间序列时，可能加性分解是不合适的，因为季节运动往往被认为与水平成正比，而噪声分量仍然是加性进入的
```

> ***decomposition:***

$$
x_{t}=z_{t} s_{t}+u_{t}
$$

the updating equations:

$$
\begin{aligned}
&z_{t}=\alpha\left(\frac{x_{t}}{s_{t-m}}\right)+(1-\beta)\left(z_{t-1}+\tau_{t-1}\right)=z_{t-1}+\tau_{t-1}+\frac{\alpha e_{t}}{s_{t-m}} \\
&\tau_{t}=\beta\left(z_{t}-z_{t-1}\right)+(1-\beta) \tau_{t-1}=\tau_{t-1}+\frac{\alpha \beta e_{t}}{s_{t-m}} \\
&s_{t}=\delta\left(\frac{x_{t}}{z_{t}}\right)+(1-\delta) s_{t-m}=s_{t-m}+\delta(1-\alpha) \frac{e_{t}}{z_{t}}
\end{aligned}
$$

Forecasts are then given by:

$$
f_{T, h}=\left(z_{T}+\tau_{T} h\right) s_{T+h-m}
$$

