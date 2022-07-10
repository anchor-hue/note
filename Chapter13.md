> 姓名：甘缘
>
> 学号：202000820142

# Chapter 13

***Vector Autoregressions and Granger Causality(向量自回归和Granger因果关系)***



## MULTIVARIATE DYNAMIC REGRESSION MODELS(多元动态回归模型)

### note 1

> ***a multivariate dynamic regression:***

$$
\begin{aligned}
&y_{1, t}=c_{1}+a_{11} y_{1, t-1}+a_{12} y_{2, t-1}+b_{10} x_{t}+b_{11} x_{t-1}+u_{1, t} \\
&y_{2, t}=c_{2}+a_{21} y_{1, t-1}+a_{22} y_{2, t-1}+b_{20} x_{t}+b_{21} x_{t-1}+u_{2, t}
\end{aligned}
$$

> ***多元动态回归模型的一般形式为:***

$$
\mathbf{y}_{t}=\mathbf{c}+\sum_{i=1}^{p} \mathbf{A}_{i} \mathbf{y}_{t-i}+\sum_{i=0}^{q} \mathbf{B}_{i} \mathbf{x}_{t-i}+\mathbf{u}_{t}
$$

其中
$$
\mathbf{A}_{i}=\left[\begin{array}{cccc}
a_{11, i} & a_{12, i} & \ldots & a_{1 n, i} \\
a_{21, i} & a_{22, i} & \ldots & a_{2 n, i} \\
\vdots & & & \vdots \\
a_{n 1, i} & a_{n 2, i} & \ldots & a_{n n, i}
\end{array}\right] \quad \mathbf{B}_{i}=\left[\begin{array}{cccc}
b_{11, i} & b_{12, i} & \ldots & b_{1 k, i} \\
b_{21, i} & b_{22, i} & \ldots & b_{2 k, i} \\
\vdots & & & \vdots \\
b_{n 1, i} & b_{n 2, i} & \ldots & b_{n k, i}
\end{array}\right]
$$

> *** symmetric n × n error covariance matrix:***

$$
\boldsymbol{\Omega}=E\left(\mathbf{u}_{t} \mathbf{u}_{t}^{\prime}\right)=\left[\begin{array}{cccc}
\sigma_{1}^{2} & \sigma_{12} & \ldots & \sigma_{1 n} \\
\sigma_{12} & \sigma_{2}^{2} & \ldots & \sigma_{2 n} \\
\vdots & & & \vdots \\
\sigma_{1 n} & \sigma_{2 n} & \ldots & \sigma_{n}^{2}
\end{array}\right]
$$

## VECTOR AUTOREGRESSIONS(向量自回归)

### note 2

there are p lags of the endogenous variables in every equation:
$$
\mathbf{y}_{t}=\mathbf{c}+\sum_{i=1}^{p} \mathbf{A}_{i} \mathbf{y}_{t-i}+\mathbf{u}_{t}
$$
roots of the characteristic equation:
$$
\mathbf{A}(B)=\mathbf{I}_{n}-\mathbf{A}_{1} B-\cdots-\mathbf{A}_{p} B^{p}=\mathbf{0}
$$


## GRANGER CAUSALITY(格兰杰因果关系 )

### note 3

```
Ai矩阵中存在非零非对角线元素，变量之间存在动态关系，否则模型将崩溃为一组n个单变量AR过程。这种动态关系的存在被称为格兰杰因果关系。
格兰杰因果关系是“可预测性”的一个标准。如果yr也导致了ys，则这对变量被称为呈现反馈。
```



## DETERMINING THE LAG ORDER OF A VECTOR AUTOREGRESSION(确定向量的滞后阶数自回归)

## note 4

> ***error covariance matrix:***

$$
\hat{\boldsymbol{\Omega}}_{p}=(T-p)^{-1} \hat{\mathbf{U}}_{p} \hat{\mathbf{U}}_{p}^{\prime}
$$

> *** likelihood ratio (LR) statistic:***

$$
L R(p, m)=(T-n p) \log \left(\frac{\left|\hat{\boldsymbol{\Omega}}_{m}\right|}{\left|\hat{\boldsymbol{\Omega}}_{p}\right|}\right) \sim \chi_{n^{2}(p-m)}^{2}
$$

> *** the multivariate AIC and BIC criteria:***

$$
\begin{aligned}
&\operatorname{MAIC}(p)=\log \left|\hat{\boldsymbol{\Omega}}_{p}\right|+\left(2+n^{2} p\right) T^{-1} \\
&\operatorname{MBIC}(p)=\log \left|\hat{\Omega}_{p}\right|+n^{2} p T^{-1} \ln T \quad p=0,1, \ldots, p_{\max }
\end{aligned}
$$



## VARIANCE DECOMPOSITIONS AND INNOVATION ACCOUNTING(预测方差分解)

### note 5

```
系数的数量会迅速增加(每一个额外的滞后会引入一个进一步的n2系数)。
```

VAR写成滞后操作符的形式为:
$$
\mathbf{A}(B) \mathbf{y}_{t}=\mathbf{u}_{t}
$$

$$
\mathbf{A}(B)=\mathbf{I}_{n}-\mathbf{A}_{1} B-\cdots-\mathbf{A}_{p} B^{p}
$$

> ***the (infinite order) VMA representation:***

$$
\mathbf{y}_{t}=\mathbf{A}^{-1}(B) \mathbf{u}_{t}=\Psi(B) \mathbf{u}_{t}=\mathbf{u}_{t}+\sum_{i=1}^{\infty} \Psi_{i} \mathbf{u}_{t-i}
$$

其中
$$
\boldsymbol{\Psi}_{i}=\sum_{j=1}^{i} \mathbf{A}_{j} \boldsymbol{\Psi}_{i-j} \quad \boldsymbol{\Psi}_{0}=\mathbf{I}_{n} \quad \boldsymbol{\Psi}_{i}=\mathbf{0} \quad i<0
$$
VMA表示重新规范化为递归形式:
$$
\mathbf{y}_{t}=\sum_{i=0}^{\infty}\left(\boldsymbol{\Psi}_{i} \mathbf{S}\right)\left(\mathbf{S}^{-1} \mathbf{u}_{t-i}\right)=\sum_{i=0}^{\infty} \boldsymbol{\Psi}_{i}^{o} \mathbf{v}_{t-i}
$$
each impulse response:
$$
\psi_{r s, i}^{O}=\mathbf{e}^{\prime}{ }_{r} \boldsymbol{\Psi}_{i} \mathbf{S e}_{s}
$$

> ***The (accumulated) long-run response:***

$$
\psi_{r s}^{O}(\infty)=\sum_{i=0}^{\infty} \mathbf{e}^{\prime}{ }_{r} \boldsymbol{\Psi}_{i} \mathbf{S e}_{s}
$$

entire set of long-run:
$$
\Psi^{o}(\infty)=\sum_{i=0}^{\infty} \boldsymbol{\Psi}_{i} \mathbf{S}=\boldsymbol{\Psi}(1) \mathbf{S}
$$

### note 6

> ***generalized impulse responses:***

$$
\psi_{r s, i}^{G}=\sigma_{r}^{-1} \mathbf{e}_{r}^{\prime} \boldsymbol{\Psi}_{i} \boldsymbol{\Omega}_{p} \mathbf{e}_{s}
$$

```
广义脉冲响应对变量的排序是不变的，是唯一的，并充分解释了不同冲击之间观察到的历史关联模式。只有当Ωp是对角线时，正交和广义脉冲响应才重合，一般来说，只有s=1是相同的。
```



## STRUCTURAL VECTOR AUTOREGRESSIONS(结构向量自回归)

### note 7

> ***A more general formulation:***

$$
\mathbf{A \mathbf { u } _ { t }}=\mathbf{B} \mathbf{v}_{t}
$$

so

$$
\mathbf{B} \mathbf{B}^{\prime}=\mathbf{A} \boldsymbol{\Omega}_{p} \mathbf{A}^{\prime}
$$

长期脉冲响应可以写成
$$
\psi_{r s}(\infty)=\sum_{i=0}^{\infty} \mathbf{e}_{r}^{\prime} \boldsymbol{\Psi}_{i} \mathbf{A}^{-1} \mathbf{B e}_{s}
$$
 in matrix form:

$$
\Psi(\infty)=\sum_{i=0}^{\infty} \Psi_{i} \mathbf{A}^{-1} \mathbf{B}=\Psi(1) \mathbf{A}^{-1} \mathbf{B}
$$

