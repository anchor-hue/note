> 姓名：甘缘
>
> 学号：202000820142

# Chapter 6

***Breaking and Nonlinear Trends(break和非线性趋势)***



## BREAKING TREND 

### note 1

> ***breaking trend model:***

$$
x_t=\mu_0+(\mu_1-\mu_0)DU_t^c+\beta_0t+\epsilon_t=\mu_0+\mu DU_t^c+\beta_0t+\epsilon_t
$$

> ***segmented trend:***

$$
x_t=\mu_0+\beta_0+(\beta_1-\beta_0)DT_t^c+\epsilon_t=\mu_0+\beta_0t+\beta DT_t^c+\epsilon_t
$$



## BREAKING TRENDS AND UNIT ROOT TESTS(break趋势和单位根检验)

### note 2

$$
\tilde{x}_t^i,i=A,B,C
$$

i = A: a constant, t, and DU^c_t

i = B: a constant, t, and DT^c_t

$$
\tilde{x}_{t}^{i}=\tilde{\phi}^{i} \tilde{x}_{t-1}^{i}+\sum_{j=0}^{k} \gamma_{j} \mathrm{D}\left(\mathrm{TB}^{c}\right)_{t-j} \sum_{j=1}^{k} \delta_{j} \nabla \tilde{x}_{t-j}^{i} \quad i=A, C
$$
i = C: a constant, t, DU^c_t , and DT^c_t

$$
\tilde{x}_{t}^{B}=\tilde{\phi}^{i} \tilde{x}_{t-1}^{B}+\sum_{j=1}^{k} \delta_{j} \nabla \tilde{x}_{t-j}^{B}+a_{t}
$$


```
注：可以使用ADF回归框架的直接扩展来执行单位根的存在性测试，以适当地纳入虚拟变量:
```

$$
\begin{aligned}
&x_{t}=\mu^{A}+\theta^{A} \mathrm{DU}_{t}^{c}+\beta^{A} t+d^{A} \mathrm{D}\left(\mathrm{TB}^{c}\right)_{t}+\phi^{A} x_{t-1}+\sum_{i=1}^{k} \delta_{i} \nabla x_{t-i}+a_{t} \\
&x_{t}=\mu^{B}+\theta^{B} \mathrm{DU}_{t}^{c}+\beta^{B} t+\gamma^{B} \mathrm{DT}_{t}^{c}+\phi^{B} x_{t-1}+\sum_{i=1}^{k} \delta_{i} \nabla x_{t-i}+a_{t} \\
&x_{t}=\mu^{c}+\theta^{C} \mathrm{DU}_{t}^{c}+\beta^{c} t+\gamma^{C} \mathrm{DT}_{t}^{c}+d^{C} \mathrm{D}\left(\mathrm{TB}^{c}\right)_{t}+\phi^{c} x_{t-1}+\sum_{i=1}^{k} \delta_{i} \nabla x_{t-i}+a_{t}
\end{aligned}
$$



### note 3

> ***(Perron)假设可以参数化为:***

$$
x_t=\eta_t+\epsilon_t
\\
\eta_t=\mu_t+\beta_tt
\\
\nabla \mu_t=v(B)v_t
\\
\nabla\beta_t=\omega(B)\omega_t
$$

其中，
$$
\phi(B)\epsilon_t=\theta(B)a_t
$$

```
注：
趋势函数的截距和斜率，是平稳可逆的积分过程。
```



## UNIT ROOTS TESTS WHEN THE BREAK DATE IS UNKNOWN(当break date未知时进行单位根检验)

### note 4

```
method1：
第一种方法选择\hat{T}_b作为最可能拒绝单位根假设的中断日期，这是检验φ = 1的T统计量最小(即最负)的日期。
method2:
第二种方法是选择\hat{T}_b作为破缺日期，其中检验break参数显著性的统计量最大。
```



## ROBUST TESTS FOR A BREAKING TREND(对breaking趋势的稳健测试)

### note 5

> ***weighted average of two statistics:***

$$
t_{\lambda}=\lambda\left(S_{0}\left(\tau^{c}\right), S_{1}\left(\tau^{c}\right)\right) \times\left|t_{0}\left(\tau^{c}\right)\right|+\left(1-\lambda\left(S_{0}\left(\tau^{c}\right), S_{1}\left(\tau^{c}\right)\right)\right) \times\left|t_{1}\left(\tau^{c}\right)\right|
$$

> ***weight function:***

$$
\lambda\left(S_{0}\left(\tau^{c}\right), S_{1}\left(\tau^{c}\right)\right)=\exp \left(-\left(500 S_{0}\left(\tau^{c}\right) S_{1}\left(\tau^{c}\right)\right)^{2}\right)
$$

$$
\tau^{c}未知但假定位于0<\tau_{\min}， \tau_{\max}<1时
$$

$$
t_{\lambda}=\lambda\left(S_{0}(\hat{\tau}), S_{1}(\tilde{\tau})\right) \times\left|t_{0}(\hat{\tau})\right|+m_{\xi}\left(1-\lambda\left(S_{0}(\hat{\tau}), S_{1}(\tilde{\tau})\right)\right) \times\left|t_{1}(\tilde{\tau})\right|
$$

## CONFIDENCE INTERVALS FOR THE BREAK DATE AND MULTIPLE BREAKS(多个断点的置信区间)

### note 6

> ***for the segmented trend model (B) and I(1) errors:***

$$
\sqrt{T}\left(\hat{\tau}-\tau^{c}\right) \stackrel{d}{\sim} N\left(0,2 \sigma^{2} / 15 \beta^{2}\right)
$$

> ***for I(0) errors:***

$$
T^{3 / 2}\left(\tilde{\tau}-\tau^{c}\right) \stackrel{d}{\sim} N\left(0,4 \sigma^{2} /\left(\tau^{c}\left(1-\tau^{c}\right) \beta^{2}\right)\right)
$$

$$
当错误为I(1)时，\tau^{c}的95 \%置信区间为：
\\\hat{\tau} \pm 1.96 \sqrt{\frac{2 \hat{\sigma}^{2}}{15 T \hat{\beta}^{2}}}
$$

```
注：
break date的极限分布不依赖于误差的自相关结构，只需要估计误差方差σ2。当错误为I(1)时，限制分布对break断的位置是不变的，而对于I(0)错误，限制分布依赖于break的位置，break。于是，越靠近样本中间，方差越小。
```



## NONLINEAR TRENDS(非线性趋势)

### note 7

> ***LSTR function:***

$$
S_{t}(\gamma, m)=(1+\exp (-\gamma(t-m T)))^{-1}
$$

> ***ESTR function:***

$$
S_{t}(\gamma, m)=1-\exp \left(-\gamma(t-m T)^{2}\right)
$$

> ***三种可选的平滑过渡趋势模型:***

$$
\begin{aligned}
&x_{t}=\mu_{0}+\mu S_{t}(\gamma, m)+\varepsilon_{t} \\
&x_{t}=\mu_{0}+\beta_{0} t+\mu S_{t}(\gamma, m)+\varepsilon_{t} \\
&x_{t}=\mu_{0}+\beta_{0} t+\mu S_{t}(\gamma, m)+\beta t S_{t}(\gamma, m)+\varepsilon_{t}
\end{aligned}
$$

```
注：
指定趋势分量和确定时间序列是否有单位根之间的相互作用是相当重要的
```



### note 8

> ***推导线性的零值对非线性趋势的替代的检验：***

$$
H_{0}: \gamma_{1 f}=\gamma_{2 f}=0, \quad f=1, \ldots, n
$$

against
$$
H_{1} \text { : at least one of } \gamma_{1 f}, \gamma_{2 f} \neq 0, \quad f=1, \ldots, n
$$

$$
z_{t}=\mu t+\beta y_{t}+\sum_{f=1}^{n} \gamma_{1 f} \sum_{s=1}^{t} \sin \left(\frac{2 \pi f s}{T}\right)+\sum_{f=1}^{n} \gamma_{2 f} \sum_{s=1}^{t} \cos \left(\frac{2 \pi f s}{T}\right)+\eta_{t}
$$

```
注：
该检验对于εt是否包含单位根是稳健的
```

> *** A suitable test of H0 against H1：***

$$
W_{0}^{n}=\frac{\operatorname{RSS}_{R}-\mathrm{RSS}_{U}}{\operatorname{RSS}_{U} / T}
$$

> *** modification:***

$$
M W_{0}^{n}=T^{-1} W_{0}^{n} \exp \left(-b_{\xi} /|D F|\right)
$$

```
注:DF is the Dickey-Fuller t-statistic testing φ=0 from the OLS regression
```

$$
\nabla e_{t}=\phi e_{t-1}+\sum_{i=1}^{k} \delta_{i} \nabla e_{t-i}+a_{t}
$$

```
注：e_t being the residuals from OLS estimation
```

> ***A method of  determining n:***

$$
H_{0}^{*}: \gamma_{1 m}=\gamma_{2 m}=0 ; \quad \gamma_{1 f}, \gamma_{2 f}, f=1, \ldots, m-1 \text { unrestricted }
$$

against

$$
H_{1}^{*} \text { :at least one of } \gamma_{1 m}, \gamma_{2 m} \neq 0
$$

> ***tested by the Wald statistic:***

$$
W_{m-1}^{m}=\frac{\mathrm{RSS}_{R}-\mathrm{RSS}_{U}}{\mathrm{RSS}_{U} / T}
$$

> ***modified statistic:***

$$
M W_{m-1}^{m}=T^{-1} W_{m-1}^{m} \exp \left(-\frac{b_{\xi}}{|D F|}\right)
$$

### note 9

使用模型选择准则来确定n。拟合两个回归序列:

> ***first:***

$$
\begin{aligned}
\nabla x_{t}=& \mu+\beta t+\phi x_{t-1}+\sum_{f=1}^{n} \gamma_{1 f} \sin \left(\frac{2 \pi f t}{T}\right)+\sum_{f=1}^{n} \gamma_{2 f} \cos \left(\frac{2 \pi f t}{T}\right) \\
&+\sum_{i=1}^{k} \delta_{i} \nabla x_{t-i}+\varepsilon_{t}
\end{aligned}
$$

> ***second:***

$$
\phi=0 \ imposed, 
\\for n=\left\{0,1, \ldots, 
\\n_{\max }\right\},
\\k=\left\{0,1, \ldots, k_{\max }\right\}
$$

