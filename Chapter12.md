> 姓名：甘缘
>
> 学号：202000820142

# Chapter 12

***Transfer Functions and Autoregressive Distributed Lag Modeling(转移函数和自回归分布滞后建模)***



## TRANSFER FUNCTION-NOISE MODELS(FUNCTION-NOISE转移模型)

### note 1

> ***single-input transfer function-noise model:***

$$
y_{t}=v(B) x_{t}+n_{t}
$$

```
假设输入和输出变量在经过适当的变换后都是平稳的。然而，两者之间的关系不是确定性的——相反，它会被随机过程nt捕获的噪声所污染，后者通常是串行相关的。一个关键假设是，xt和nt是独立的，因此过去的x影响未来的y，但反过来不影响未来的y，因此排除了y对x的反馈。
```

written as the rational distributed lag:
$$
v(B)=\frac{\omega(B) B^{b}}{\delta(B)}
$$
the numerator and denominator polynomials:

$$
\omega(B)=\omega_{0}-\omega_{1} B-\cdots-\omega_{s} B^{s}
$$

and

$$
\delta(B)=1-\delta_{1} B-\cdots-\delta_{r} B^{r}
$$

### note 2

假设噪声过程遵循ARMA (p, q)模型:
$$
n_{t}=\frac{\theta(B)}{\phi(B)} a_{t}
$$

> ***the combined transfer function-noise model:***

$$
y_{t}=\frac{\omega(B)}{\delta(B)} x_{t-b}+\frac{\theta(B)}{\phi(B)} a_{t}
$$

model:
$$
y_{t}=\sum_{j=1}^{M} v_{j}(B) x_{j, t}+n_{t}=\sum_{j=1}^{M} \frac{\omega_{j}(B) B^{b_{j}}}{\delta_{j}(B)} x_{j, t}+\frac{\theta(B)}{\phi(B)} a_{t}
$$

其中

$$
\omega_{j}(B)=\omega_{j, 0}-\omega_{j, 1} B-\cdots-\omega_{j, s_{j}} B^{s_{j}}
$$

and

$$
\delta_{j}(B)=1-\delta_{j, 1} B-\cdots-\delta_{j, r_{j}} B^{r_{j}}
$$



## AUTOREGRESSIVE DISTRIBUTED LAG MODELS(自回归分布滞后模型)

### note 3

> ***autoregressive distributed lag(ARDL):***



$$
\delta_{1}(B)=\cdots=\delta_{M}(B)=\phi(B) \quad \theta(B)=1
$$

$$
\phi(B) y_{t}=\beta_{0}+\sum_{j=1}^{M} \beta_{j}(B) x_{j, t}+a_{t}
$$

written as:
$$
y_{t}=\beta_{0}+\sum_{i=1}^{p} \phi_{i} y_{t-i}+\sum_{j=1}^{M} \beta_{j}(1) x_{j, t}+\sum_{j=1}^{M} \tilde{\beta}_{j}(B) \nabla x_{j, t}+a_{t}
$$
Solving for y_{t} then yields

$$
y_{t}=\theta_{0}+\sum_{j=1}^{M} \theta_{j} x_{j, t}+\sum_{j=1}^{M} \tilde{\theta}_{j}(B) \nabla x_{j, t}+\varepsilon_{t}
$$

有

$$
\begin{gathered}
\theta_{0}=\phi^{-1}(1) \beta_{0} \\
\theta_{j}=\phi^{-1}(1) \beta_{j}(1) \\
=\phi^{-1}(B)\left(\tilde{\beta}_{j}(B)-\tilde{\phi}(B) \phi^{-1}(1) \beta_{j}(1)\right) \quad j=1, \ldots, M \\
\varepsilon_{t}=\phi^{-1}(B) a_{t}
\end{gathered}
$$

其中

$$
\tilde{\phi}(B)=\nabla^{-1}(\phi(B)-\phi(1))
$$

estimate of the long-run relationship between y and x_j：
$$
\hat{\theta}_{j}=\frac{\hat{\beta}_{j}(1)}{1-\sum_{i=1}^{p} \hat{\phi}_{i}}=\frac{\hat{\beta}_{j, 0}+\cdots+\hat{\beta}_{j, s_{j}}}{1-\sum_{i=1}^{p} \hat{\phi}_{i}}
$$
