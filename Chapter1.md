> 姓名：甘缘
>
> 学号：202000820142

# Chapter 1 

**Time Series and Their Features（时间序列及其特征）**



### **note 1**

> ***a time series on some variable x will be denoted as:***

$$
x_t\  ,\ t = 1,2,...,T
$$

> ***observation period：***

$$
t = 1,2,...,T
$$

```
注：
1.t = 1 是对x的第一个观测，t = T 是对x的最后一个观测
2.t通常以等间隔测量
```

### note 2

> ***forecast horizon：***

$$
h 
$$

>  ***unknown values of t at times T + 1,  T + 2, ..., T+h***



## 1. Autocorrelation and Periodic Movements(自相关和周期运动)



### note 3

> ***The lag-k (sample) autocorrelation is defined as:***

$$
r_k = \frac{\sum_{t=k+1}^{T}(x_t-\bar{x})(x_{t-k}-\bar{x})}{Ts^2}
$$

> ***sample mean***

$$
\bar{x} = T^{-1}\sum_{t=1}^Tx_t
$$

> ***sample variance***

$$
s^2 = T^{-1}\sum_{t=1}^T(x_t-\bar{x})^2
$$

> ***sample autocorrelation function (SACF):***

$$
不同k值的样本自相关集合
$$



## 2. Seasonality( 季节性)



> ***当一个时间序列以每月或每季度的间隔观察时，每年的 seasonal pattern 往往是一个重要的特征***



## 3. Stationarity and Nonstationarity(平稳性和非平稳)



### note 4

> ***constant mean level 是序列 stationary 的必要条件***

> ***如果 mean level 不是 constant，那么序列是 nonstationary***



## 4. Trends(趋势)



### note 5

> ***linear trends: has  reasonably constant slopes***

> ***nonlinear:  has a nonconstant slope***



## 5. Volatility(波动性)



### note 6

> ***constant variance 是序列 stationary 的又一个必要条件***

> ***可以通过 Forecasting With Univariate Models 对随时间变化的 variance 进行建模***



## 6. Common Features(共同特征)



### note 7

> ***cointegrate: share a common trend***



## 7. Time Series Having Natural Constrains(有自然约束的时间序列)



### note 8

> ***compositional time series:***
>
> ***e.g. lie between zero and one and must also add up to one for each observation***

### note 9

> ***counts: series occur naturally as (small) integers, 不连续***





















