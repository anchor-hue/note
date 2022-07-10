> 姓名：甘缘
>
> 学号：202000820142

# Chapter 8

***Unobserved Component Models, Signal Extraction, and Filters(Unobserved组件、模型、信号提取和过滤器)***



## UNOBSERVED COMPONENT MODELS(Unobserved组件模型)

### note 1

> ***A difference stationary:***

$$
x_{t}=z_{t}+u_{t}
$$

\nabla x_{t} is the stationary process:
$$
\nabla x_{t}=\mu+v_{t}+u_{t}-u_{t-1}
$$
an autocorrelation function:
$$
\rho_{1}=-\frac{\sigma_{u}^{2}}{\sigma_{u}^{2}+2 \sigma_{v}^{2}}
$$

written as the MA(1) process:

$$
\nabla x_{t}=\mu+e_{t}-\theta e_{t-1}
$$



### note 2

> ***unobserved component (UC) models:***

$$
\nabla z_{t}=\mu+\gamma(B) v_{t}
$$

and

$$
u_{t}=\lambda(B) a_{t}
$$

$$
\nabla x_{t}=\mu+\theta(B) e_{t}
$$

$$
\sigma_{e}^{2} \frac{\theta(B) \theta\left(B^{-1}\right)}{(1-B)\left(1-B^{-1}\right)}=\sigma_{v}^{2} \frac{\gamma(B) \gamma\left(B^{-1}\right)}{(1-B)\left(1-B^{-1}\right)}+\sigma_{a}^{2} \lambda(B) \lambda\left(B^{-1}\right)
$$

```
注：
即使方差被识别，这样的分解可能并不总是可行的。
```

### note 3

> ***Wold decomposition：***

$$
\nabla x_{t}=\mu+\psi(B) e_{t}=\mu+\sum_{j=0}^{\infty} \psi_{j} e_{t-j}
$$

since:
$$
\psi(B)=\psi(1)+C(B)
$$
so that:

$$
\begin{aligned}
C(B) &=\psi(B)-\psi(1) \\
&=1+\psi_{1} B+\psi_{2} B^{2}+\psi_{3} B^{3}+\cdots-\left(1+\psi_{1}+\psi_{2}+\psi_{3}+\cdots\right) \\
&=-\psi_{1}(1-B)-\psi_{2}\left(1-B^{2}\right)-\psi_{3}\left(1-B^{3}\right)-\cdots \\
&=(1-B)\left(-\psi_{1}-\psi_{2}(1+B)-\psi_{3}\left(1+B+B^{2}\right)-\cdots\right)
\end{aligned}
$$

that is,
$$
C(B)=(1-B)\left(-\left(\sum_{j=1}^{\infty} \psi_{j}\right)-\left(\sum_{j=2}^{\infty} \psi_{j}\right) B-\left(\sum_{j=3}^{\infty} \psi_{j}\right) B^{2}-\cdots\right)=\nabla \tilde{\psi}(B)
$$

Thus,

$$
\psi(B)=\psi(1)+\nabla \tilde{\psi}(B)
$$

implying that:

$$
\nabla x_{t}=\mu+\psi(1) e_{t}+\nabla \tilde{\psi}(B) e_{t}
$$

> ***decomposition:***

$$
\nabla z_{t}=\mu+\left(\sum_{j=0}^{\infty} \psi_{j}\right) e_{t}=\mu+\psi(1) e_{t}
$$

and

$$
u_{t}=-\left(\sum_{j=1}^{\infty} \psi_{j}\right) e_{t}-\left(\sum_{j=2}^{\infty} \psi_{j}\right) e_{t-1}-\left(\sum_{j=3}^{\infty} \psi_{j}\right) e_{t-2}-\cdots=\tilde{\psi}(B) e_{t}
$$



## SIGNAL EXTRACTION(信号提取)

### note 4

```
给定UC模型和zt和ut模型，提供这两个未观察到的成分的估计通常是有用的，这一过程被称为信号提取。
```

```
注：
如果我们只得到xt及其模型的实现，那么zt和ut的组件模型一般是未知的。
```

### note 5

If xt follows the ARIMA(0,1,1) process：
$$
\nabla x_{t}=(1-\theta B) e_{t}
$$

> ***the most general signal-plus-white-noise UC model：***

$$
\nabla z_{t}=(1-\Theta B) v_{t}
$$

```
注：
canonical decomposition of x_t
```

> ***imply:***

$$
\gamma(B)=1+B
$$

$$
\hat{z}_{t}=\frac{\sigma_{v}^{2}(1+B)\left(1+B^{-1}\right)}{\sigma_{e}^{2}(1-\theta B)\left(1-\theta B^{-1}\right)}
$$

and
$$
(1-\theta B) \zeta_{t}=(1+B) \xi_{t} .
$$

### note 6

> ***semi-infinite sample:***

$$
\left\{x_{s}, s \leq t-m\right\}
$$

> ***an estimate of z_t:***

$$
\hat{z}_{t}^{(m)}=\nu_{z}^{(m)}(B) x_{t}
$$

其中

$$
\nu_{z}^{(m)}(B)=\frac{(1-B)}{\sigma_{e}^{2} \theta(B)}\left[\frac{\sigma_{v}^{2} \gamma(B) \gamma\left(B^{-1}\right)}{(1-B) \theta\left(B^{-1}\right)}\right]_{m}
$$

notation:

$$
[h(B)]_{m}=\sum_{j=m}^{\infty} h_{j} B^{j}
$$

 for the Muth model :

$$
\nu_{z}^{(m)}(B)=\frac{\sigma_{v}^{2}(1-B)}{\sigma_{e}^{2}(1-\theta B)}\left[\frac{(1-B)^{-1}}{\left(1-\theta B^{-1}\right)}\right]_{m}
$$

Pierce (1979) shows

$$
\nu_{z}^{(m)}(B)=\frac{\sigma_{v}^{2} B^{m}}{\sigma_{e}^{2}(1-\theta)} \sum_{j=0}^{\infty}(\theta B)^{j}=(1-\theta) B^{m} \sum_{j=0}^{\infty}(\theta B)^{j}
$$

m<0时：

$$
\nu_{z}^{(m)}(B)=\theta^{-m}(1-\theta) B^{m} \sum_{j=0}^{\infty}(\theta B)^{j}+\frac{1}{(1-\theta B)} \sum_{j=0}^{-m-1} \theta^{j} B^{-j}
$$

```
注：
我们对观测序列应用指数加权移动平均，从最近的可用数据开始，但不依赖于m的值。
```



## FILTERS(过滤器)

### note 7

> ***Hodrick-Prescott (H-P) trend estimator:***

$$
\hat{z}_{t}(\lambda)=\left(1+\lambda(1-B)^{2}\left(1-B^{-1}\right)^{2}\right)^{-1} x_{t}
$$

> ***MMSE trend estimator：***

$$
\hat{z}_{t}=\frac{\sigma_{\nu}^{2} \gamma(B) \gamma\left(B^{-1}\right)}{\sigma_{e}^{2} \theta(B) \theta\left(B^{-1}\right)} x_{t}=\frac{\gamma(B) \gamma\left(B^{-1}\right)}{\gamma(B) \gamma\left(B^{-1}\right)+\left(\sigma_{a}^{2} / \sigma_{\nu}^{2}\right) \lambda(B) \lambda\left(B^{-1}\right)} x_{t}
$$



### note 8

> ***linear filter：***

$$
y_{t}=\sum_{j=-n}^{n} a_{j} x_{t-j}=\left(a_{-n} B^{-n}+a_{-n+1} B^{-n+1}+\cdots+a_{0}+\cdots+a_{n} B^{n}\right) x_{t}=a(B) x_{t}
$$

### note 9

> ***power transfer function :***

$$
|a(\omega)|^{2}=\left(\sum_{j} a_{j} \cos \omega j\right)^{2}+\left(\sum_{j} a_{j} \sin \omega j\right)^{2}
$$

### note 10

an “ideal” low-pass filter has the frequency response function:
$$
a_{L}(\omega)= \begin{cases}1 & \text { if } \omega<\omega_{c} \\ 0 & \text { if } \omega>\omega_{\mathrm{c}}\end{cases}
$$
The ideal low-pass filter will take the form:

$$
a_{L}(B)=\frac{\omega_{c}}{\pi}+\sum_{j=1}^{\infty} \frac{\sin \omega_{c} j}{\pi j}\left(B^{j}+B^{-j}\right)
$$

The H-P trend-extraction filter has the frequency response function:
$$
a_{\mathrm{H}-\mathrm{P}}(\omega)=\frac{1}{1+4 \lambda(1-\cos \omega)^{2}}
$$


### note 11

> ***band-pass filter:***

$$
a_{B}(B)=\frac{\omega_{c, 2}-\omega_{c, 1}}{\pi}+\sum_{j=1}^{\infty} \frac{\sin \omega_{c, 2} j-\sin \omega_{c, 1} j}{\pi j}\left(B^{j}+B^{-j}\right)
$$

with weights:
$$
\begin{aligned}
&a_{B, 0}=a_{c, 2,0}-a_{c, 1,0}=\frac{4}{3}-\frac{1}{4}-\left(\zeta_{c, 2, n}-\zeta_{c, 1, n}\right) \\
&a_{B, j}=a_{c, 2, j}-a_{c, 1, j}=\frac{1}{\pi j}\left(\sin \frac{4 \pi j}{3}-\sin \frac{\pi j}{4}\right)-\left(\zeta_{c, 2, n}-\zeta_{c, 1, n}\right) \quad j=1, \ldots, n
\end{aligned}
$$

其中

$$
\zeta_{c, i, n}=-\frac{\sum_{j=-n}^{n} a_{c, i, n}}{2 n+1} \quad i=1,2
$$

