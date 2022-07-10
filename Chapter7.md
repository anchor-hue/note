> 姓名：甘缘
>
> 学号：202000820142

# Chapter 7

***An Introduction to Forecasting With Univariate Models(预测概论与单变量模型)***



## FORECASTING WITH AUTOREGRESSIVE-INTEGRATED-MOVING AVERAGE (ARIMA) MODELS(利用自回归综合移动平均模型进行预测)

### note 1

suppose we have a realization:
$$
\left(x_{1-d}, x_{2-d}, \ldots, x_{T}\right)
$$
from a general ARIMA (p,d,q) process:
$$
\phi(B) \nabla^{d} x_{t}=\theta_{0}+\theta(B) a_{t}
$$
 let：
$$
\alpha(B)=\phi(B) \nabla^{d}=\left(1-\alpha_{1} B-\alpha_{2} B^{2}-\cdots-\alpha_{p+d} B^{p+d}\right)
$$

then：
$$
\alpha(B) x_{T+h}=\theta_{0}+\theta(B) a_{T+h}
$$

that is,

$$
\begin{aligned}
x_{T+h}=& \alpha_{1} x_{T+h-1}+\alpha_{2} x_{T+h-2}+\cdots+\alpha_{p+d} x_{T+h+p-d}+\theta_{0}+a_{T+h} \\
&-\theta_{1} a_{T+h-1}-\cdots-\theta_{q} a_{T+h-q}
\end{aligned}
$$

$$
\begin{aligned}
f_{T, h}=& E\left(\alpha_{1} x_{T+h-1}+\alpha_{2} x_{T+h-2}+\cdots+\alpha_{p+d} x_{T+h-p-d}+\theta_{0}\right.\\
&\left.+a_{T+h}-\theta_{1} a_{T+h-1}-\cdots-\theta_{q} a_{T+h-q} \mid x_{T}, x_{T-1}, \ldots\right) .
\end{aligned}
$$

### note 2

$$
E\left(x_{T+j} \mid x_{T}, x_{T-1}, \ldots\right)=\left\{\begin{array}{ll}
x_{T+j}, & j \leq 0 \\
f_{T, j}, & j>0
\end{array},\right.
$$

and

$$
E\left(a_{T+j} \mid x_{T}, x_{T-1}, \ldots\right)=\left\{\begin{array}{cc}
a_{T+j}, & j \leq 0 \\
0, & j>0
\end{array},\right.
$$

```
注：
(1) replace past expectations (j＜=0) by known values, x_{T+j} and a_{T+j} 
(2) replace future expectations (j>0) by forecast values, f_{T, j} and 0
```



### note 3

> ***h-step ahead forecast error for origin T:***

$$
e_{T, h}=x_{T+h}-f_{T, h}=a_{T+h}+\psi_{1} a_{T+h-1}+\cdots+\psi_{h-1} a_{T+1}
$$

> ***one-step ahead forecast error:***

$$
e_{T, 1}=x_{T, 1}-f_{T, 1}=a_{T+1} 
$$

```
注：
对于MMSE预测，提前一步的预测误差必须是不相关的
```

the variance of the forecast error：
$$
V\left(e_{T, h}\right)=\sigma^{2}\left(1+\psi_{1}^{2}+\psi_{2}^{2}+\cdots+\psi_{h-1}^{2}\right)
$$
For the ARIMA(0,1,1) process：
$$
V\left(e_{T, h}\right)=\sigma^{2}\left(1+(h-1)(1-\theta)^{2}\right)
$$
the ARIMA(0,2,2) model：
$$
\begin{aligned}
V\left(e_{T, h}\right)=& \sigma^{2}\left(1+(h-1)\left(1+\theta_{2}\right)^{2}+\frac{1}{6} h(h-1)(2 h-1)\left(1-\theta_{1}-\theta_{2}\right)^{2}\right.\\
&\left.+h(h-1)\left(1+\theta_{2}\right)\left(1-\theta_{1}-\theta_{2}\right)\right)
\end{aligned}
$$

```
注：
随着预测视界的增加，预测不确定性可能大幅增加。
```



## FORECASTING A TREND STATIONARY PROCESS(预测趋势平稳过程)

### note 4

> *** trend stationary (TS) process:***

$$
x_{t}=\beta_{0}+\beta_{1} t+\varepsilon_{t} \quad \phi(B) \varepsilon_{t}=\theta(B) a_{t}
$$

forecast of x_{T+h}:
$$
f_{T, h}=\beta_{0}+\beta_{1}(T+h)+g_{T, h}
$$
the forecast of ε_{T+h}:
$$
\begin{aligned}
g_{T, h}=& E\left(\phi_{1} \varepsilon_{T+h-1}+\phi_{2} \varepsilon_{T+h-2}+\cdots+\phi_{p} x_{T+h-p}+a_{T+h}\right.\\
&\left.-\theta_{1} a_{T+h-1}-\cdots-\theta_{q} a_{T+h-q} \mid \varepsilon_{T}, \varepsilon_{T-1}, \ldots\right)
\end{aligned}
$$

> ***forecast error:***

$$
e_{T, h}=x_{t}-f_{T, h}=\varepsilon_{T+h}-g_{T, h}
$$

```
注：
在任何TS预测的不确定性是由于预测ARMA组件的误差
```

