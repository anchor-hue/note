> 姓名：甘缘
>
> 学号：202000820142

# Chapter 14

***Error Correction, Spurious Regressions, and Cointegration(向纠错,伪回归和协整)***



## THE ERROR CORRECTION FORM OF AN AUTOREGRESSIVE DISTRIBUTED LAG MODEL(一种自回归的错误修正形式分布滞后模型)

### note 1

> ***ARDL(1,1):***

$$
y_{t}=\beta_{0}+\phi y_{t-1}+\beta_{1,0} x_{t}+\beta_{1,1} x_{t-1}+a_{t}
$$

recast this ARDL:
$$
\nabla y_{t}=\beta_{0}-(1-\phi) y_{t-1}+\left(\beta_{1,0}+\beta_{1,1}\right) x_{t-1}+\beta_{1,0} \nabla x_{t}+a_{t}
$$
or

$$
\nabla y_{t}=\beta_{1,0} \nabla x_{t}-(1-\phi)\left(y_{t-1}-\frac{\beta_{0}}{1-\phi}-\frac{\beta_{1,0}+\beta_{1,1}}{1-\phi} x_{t-1}\right)+a_{t}
$$

i.e., as

$$
\nabla y_{t}=\beta_{1,0} \nabla x_{t}-(1-\phi)\left(y_{t-1}-\theta_{0}-\theta_{1} x_{t-1}\right)+a_{t}
$$

### note 2

```
如果平衡关系的参数未知，则可以用非线性最小二乘估计，也可以用ECM表示
```

$$
\nabla y_{t}=\beta_{0}+\beta_{1,0} \nabla x_{t}+\gamma\left(y_{t-1}-x_{t-1}\right)+\delta x_{t-1}+a_{t}
$$

 error correction:
$$
e c_{t}=y_{t}-\theta_{0}-\sum_{j=1}^{M} \theta_{j} x_{j, t}
$$
generalizes to

$$
\begin{aligned}
\nabla y_{t}=& \beta_{0}-\phi(1) e c_{t-1}+\phi^{*}(B) \nabla y_{t-1}+\sum_{j=1}^{M} \tilde{\beta}_{j}(B) \nabla x_{j, t-1} \\
&+\sum_{j=1}^{M} \beta_{j}(B) \nabla x_{j, t}+a_{t}
\end{aligned}
$$

其中

$$
\phi^{*}(B)=\sum_{i=1}^{p} \phi_{i} B^{i}=\phi(B)-1
$$

## SPURIOUS REGRESSIONS(伪回归)

### note 3

```
传递函数和自回归分布
滞后建模，它已经隐含地假设所有进入ARDL/ECM的变量都是平稳的，因此任何非平稳序列都已经预先适当地进行了区分。
```

> ***DGP:***

$$
\begin{gathered}
y_{t}=\phi y_{t-1}+u_{t} \quad u_{t} \sim \text { i.i.d. }\left(0, \sigma_{u}^{2}\right) \\
x_{t}=\phi^{*} x_{t-1}+v_{t} \quad v_{t} \sim \text { i.i.d. }\left(0, \sigma_{v}^{2}\right) \\
E(u_tv_s)=0 \text { for all } t, s \quad E\left(u_{t} u_{t-k}\right)=E\left(v_{t} v_{t-k}\right)=0 \text { for all } k \neq 0
\end{gathered}
$$

> *** regression model:***

$$
y_{t}=\beta_{0}+\beta_{1} x_{t}+\varepsilon_{t}
$$

```
注：
事实上，随着独立随机游动次数的增加，在传统的显著性水平上拒绝无关系的null的次数比例也增加了。
同的任意大样本会产生随机不同的β1估计。β0的分布实际上是发散的，因此估计可能会越来越远。
```



### note 4

在回归中加入时间趋势来缓解与非平稳回归相关的伪回归问题:
$$
y_{t}=\beta_{0}+\beta_{1} x_{t}+\theta t+\varepsilon_{t}
$$


## ERROR CORRECTION AND COINTEGRATION(误差校正和协整)

### note 5

the linear combination:
$$
e_{t}=y_{t}-a x_{t}
$$

```
注：
协整的概念可以与长期均衡的概念相联系。
```

### note 6

> ***(contemporaneous) innovation covariance matrix:***

$$
\boldsymbol{\Sigma}=\left[\begin{array}{cc}
\sigma_{u}^{2} & \sigma_{u v} \\
\sigma_{u v} & \sigma_{v}^{2}
\end{array}\right]
$$

it is singular then

$$
|\boldsymbol{\Sigma}|=\sigma_{u}^{2} \sigma_{v}^{2}-\sigma_{u v}^{2}=0
$$



## TESTING FOR COINTEGRATION(协整检验)

### note 7

```
考虑到协整在具有集成变量的回归模型中发挥的关键作用，检验其存在显然是重要的。
```

> ***检验可以基于协整回归的残差，即:***

$$
\hat{e}_{t}=y_{t}-\hat{\beta}_{0}-\hat{\beta}_{1} x_{1, t}-\cdots-\hat{\beta}_{M} x_{M, t}
$$

```
注：
影响临界值的另一个因素是回归子M的个数。
```

 ### note 8

> ***The conditional error correction (CEC) form of an ARDL model:***

$$
\begin{aligned}
\nabla y_{t}=& \alpha_{0}+\alpha_{1} t-\phi(1) y_{t-1}+\sum_{j=1}^{M} \beta_{j}(1) x_{j, t-1} \\
&+\phi^{*}(B) \nabla y_{t-1}+\sum_{j=0}^{M} \gamma_{j}(B) \nabla x_{j, t}+a_{t}
\end{aligned}
$$

```
注：
当检验统计量低于较低的临界值时，不拒绝零值，并得出协整不可能的结论。如果检验统计量高于上临界值，可以拒绝零，可以得出协整的结论。但是，如果试验统计值落在下临界值和上临界值之间，则试验是不确定的，需要进行额外的分析和试验。
```



当α0 = α1 = 0时， and the CEC can be written:
$$
\nabla y_{t}=-\phi(1)\left(y_{t-1}-\sum_{j=1}^{M} \frac{\beta_{j}(1)}{\phi(1)} x_{j, t-1}\right)+\phi^{*}(B) \nabla y_{t-1}+\sum_{j=1}^{M} \gamma_{j}(B) \nabla x_{j, t}+a_{t}
$$

即

$$
\nabla y_{t}=-\phi(1) e c_{t-1}+\phi^{*}(B) \nabla y_{t-1}+\sum_{j=1}^{M} \gamma_{j}(B) \nabla x_{j, t}+a_{t}
$$

其中，the error correction:

$$
e c_{t}=y_{t}-\sum_{j=1}^{M} \frac{\beta_{j}(1)}{\phi(1)} x_{j, t}
$$



## ESTIMATING COINTEGRATING REGRESSIONS(估计协整回归)

### note 9

the cointegrating regression:
$$
y_{t}=\beta_{0}+\beta_{1} x_{1, t}+\cdots+\beta_{M} x_{M, t}+e_{t}
$$

```
注：
虽然OLS估计产生了参数的超一致估计，但它们仍然具有偏倚和不对称抽样分布，甚至渐近。
```

fully modified OLS (FM-OLS) estimator：

example：
$$
y_{t}=\beta_{0}+\sum_{j=1}^{M} \beta_{j, t} x_{j, t}+\sum_{i=1}^{p} \gamma_{i} \nabla y_{t-i}+\sum_{j=1}^{M} \sum_{i=-p_{1}}^{p_{2}} \delta_{j, i} \nabla x_{j, t-i}+e_{t}
$$
