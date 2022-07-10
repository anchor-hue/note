> 姓名：甘缘
>
> 学号：202000820142

# Chapter 3

***ARMA Models(自回归移动平均模型) for Stationary Time Series***



## 1.STOCHASTIC PROCESSES AND STATIONARITY(随机过程与平稳性)



### note 1

> ***T means:***

$$
E(x_1),E(x_2),...,E(x_T)
$$

> ***T variance:***

$$
V(X_1),V(x_2),...,V(x_T)
$$

> ***T(T-1)/2 covariances:***

$$
Cov(x_i,x_j),\ i\lt j
$$



### note 2

```
there are only T observations but T+T(T+1)/2 unknown parameters.

使用单一实现来推断联合概率分布的未知参数的过程只有在过程是遍历的情况下才有效，这大致意味着当实现的长度变得无限时，有限延伸的实现的样本矩接近其总体对应的样本矩。
```

> ***strictly stationary:***

$$
如果一个随机过程的性质不受时间原点变化的影响，
\\ 即任意一组时间t_1,t_2,...,t_m的联合概率分布
\\必须与t_{1+k},t_{2+k},...,t_{m+k}的联合概率分布相同,
\\其中k是时间上的任意位移
\\则该随机过程被称为严格平稳的.
$$

> ***if m=1:***

$$
E(x_1)=E(x_2)=...=E(x_T)=\mu
$$

$$
V(x_1)=V(x_2)=...=V(x_T)=\sigma_x^2
$$



> ***if m=2:***

$$
Cov(x_1,x_{1+k})=Cov(x_2,x_{2+k})=...=Cov(x_{T-k},x_{T})=Cov(x_t,x_{t-k})
$$

> ***lag-k autocovariance :***

$$
\gamma_t=Cov(x_t,x_{t-k})=E((x_t-\mu)(x_{t-k}-\mu))
$$

$$
\gamma_0=E(x_t-\mu)^2=V(x_t)=\sigma_x^2
$$

> *** lag-k autocorrelation:***

$$
\rho_k=\frac{Cov(x_t,x_{t-k})}{(V(x_t)V(x_{t-k}))^{1/2}}=\frac{\gamma_k}{\gamma_0}=\frac{\gamma_k}{\sigma_x^2}
$$

```
注：
假设xt的均值和方差都是常数，自协方差和自相关只依赖于滞后k的集合被称为弱或协方差平稳性。

strict stationarity可以推出weak stationarity，反过来不成立。
如果可以假设联合正态性，使得分布完全由前两个矩表征，那么weak stationarity可以推出strict stationarity。 
```


$$
\gamma_k=Cov(x_t,x_{t-k})=Cov(x_{t-k},x_{t})=Cov(x_t,x_{t+k})=\gamma_{-k}
$$

$$
\rho_{-k}=\rho_k
$$



## 2.WOLD’S DECOMPOSITION AND AUTOCORRELATION(Wold分解和自相关)



### note 3

> ***Wold’s decomposition:***

$$
每一个weakly\ stationary、purely\ nondeterministic、随机过程x_t-μ，\\
可以写成不相关随机变量序列的线性组合(或线性滤波器)。
$$

> ***This linear filter representation is given by:***

$$
x_t-\mu=a_t+\psi_1a_{t-1}+\psi_2a_{t-2}+...=\sum_{j=0}^{\infty}\psi_ja_{t-j}\ \ \ \ \psi_0=1
$$

$$
其中，a_t,t=0,\pm1,\pm2,...是不相关的随机变量序列
$$

> ***white noise:***

$$
E(a_t)=0\ \ \ V(a_t)=E(a^2_t)=\sigma^2\lt\infin
$$

$$
Cov(a_t,a_{t-k})=E(a_t,a_{t-k})=0,\ \ for\ all\ k\ne0
$$

$$
a_t\sim WN(0,\sigma^2)
$$

![](./images/figure3.7_1.png)



## 3.FIRST-ORDER AUTOREGRESSIVE PROCESSES(一阶自回归过程)



### note 4

> ***first-order autoregressive process:***

![](./images/figure3.8_1.png)

> *** by using this operator the AR(1) process:***

![](./images/figure3.9_1.png)



## 4.FIRST-ORDER MOVING AVERAGE PROCESSES(一阶移动平均过程)



### note 5

> ***first-order moving average (MA(1)) process:***

![](./images/figure3.12_1.png)

> ***it follows:***

$$
\gamma_0=\sigma^2(1+\theta^2)\ \ \gamma_1=-\sigma^2\theta\ \ \gamma_k=0\ for\ k\gt1
$$

> ***its ACF:***

$$
\rho_1=-\frac{\theta}{1+\theta^2}\ \ \rho_k=0\ for\ k\gt1
$$



## 5.GENERAL AR AND MA PROCESSES(一般的AR和MA过程)



### note 6

> *** general autoregressive model of order p (AR(p)):***

$$
x_t-\phi_1x_{t-1}-\phi_2x_{t-2}-...-\phi_px_{t-p}=a_t
$$

> ***or***

$$
(1-\phi_1B-\phi_2B^2-...-\phi_pB^p)x_t=\phi(B)x_t=a_t
$$

![](./images/figure3.17_1.png)

![](./images/figure3.17_2.png)



### note 7

> ***The ACF of an AR(2) process:***

$$
\rho_k=\phi_1\rho_{k-1}+\phi_2\rho_{k-2}
$$

```
注：
一般来说，两个随机变量之间的相关性往往是由于两个变量都与第三个变量相关。 
```



### note 8

> ***The kth partial autocorrelation is the coefficient φkk in the AR(k) process:***

$$
x_t=\phi_{k1}x_{t-1}+\phi_{k2}x_{t-2}+...\phi_{kk}x_{t-k}+a_t
$$

![](./images/figure3.20_1.png)

```
注：
一个AR(p)过程被描述为:
1.ACF无限，是阻尼指数函数和阻尼正弦波的组合。
2.PACF是滞后大于p时为零。
```



## AUTOREGRESSIVE-MOVING AVERAGE MODELS(AUTOREGRESSIVE-MOVING平均模型)



### note 9

```
The ARMA process, thus, leads to both MA and autoregressive representations having an infinite number of weights.
```

```
注：
ARMA(1,1)过程的ACF类似于AR(1)过程，因为自相关以φ的速率指数衰减。 种衰变从ρ1开始，而不是从 ρ0=1 。
```



## ARMA MODEL BUILDING AND ESTIMATION(ARMA模型的建立和估计)



```
将ARMA模型拟合到观测时间序列的第一步是获得一般未知参数μ、σ^2_x和ρ_k的估计。
μ和σ^2_x可以由样本均值和样本方差估计得到，ρ_k则由给出的滞后k样本自相关提供。
```

### note 10

> ***Bartlett standard errors:***

$$
V(r_k)=T^{-1}(1+2\rho_1^2+...+2\rho_q^2)
$$

> ***Ljung and Box (1978) show :***

$$
Q(k)=T(T+2)\sum_{i=1}^k(T-i)^{-1}r_i^2
$$

```
注：Q(k)服从自由度为k的卡方分布。
```

> ***Akaike’s (1974) Information Criteria (AIC)：***

$$
AIC(p,q)=\log\sigma^2+2(p+q)T^{-1}
$$

> ***BIC of Schwarz (1978):***

$$
BIC(p,q)=\log\sigma^2+2(p+q)T^{-1}\log T
$$

## 小结

![](./images/endnotes3_1.png)



![](./images/endnotes3_2.png)









