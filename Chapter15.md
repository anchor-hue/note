> 姓名：甘缘
>
> 学号：202000820142

# Chapter 15

***Vector Autoregressions With Integrated Variables, Vector Error Correction Models, and Common Trends(向量自回归与综合变量向量错误修正模型和普遍的趋势)***



## VECTOR AUTOREGRESSIONS WITH INTEGRATED VARIABLES(带集成变量的向量自回归)

### note 1

 the n-variable VAR(p):
$$
A(B) y_{t}=c+u_{t}
$$
其中
$$
E\left(\boldsymbol{u}_{t}\right)=\mathbf{0}
$$

$$
E\left(\boldsymbol{u}_{t} \boldsymbol{u}_{s}\right)=\left\{\begin{array}{cc}
\boldsymbol{\Omega}_{p} & t=s \\
\mathbf{0} & t \neq s
\end{array}\right.
$$

the matrix polynomial:
$$
\boldsymbol{A}(B)=\boldsymbol{I}_{\boldsymbol{n}}-\sum_{i=1}^{p} \boldsymbol{A}_{\boldsymbol{i}} B^{i}
$$
 written, for p＞1, as
$$
A(B)=\left(I_{n}-A B\right)-\Phi(B) B \nabla
$$

其中

$$
\boldsymbol{A}=\sum_{i=1}^{p} \boldsymbol{A}_{i}
$$

and

$$
\boldsymbol{\Phi}(B)=\sum_{i=1}^{p-1} \boldsymbol{\Phi}_{i} B^{i-1}, \quad \boldsymbol{\Phi}_{i}=-\sum_{j=i+1}^{p} \boldsymbol{A}_{j}
$$

With this decomposition of A(B)，



$$
\left(\boldsymbol{I}_{n}-\boldsymbol{A B}-\boldsymbol{\Phi}(B) \nabla\right) \boldsymbol{y}_{t}=\boldsymbol{c}+\boldsymbol{u}_{t}
$$

or

$$
y_{t}=c+\Phi(B) \nabla y_{t-1}+A y_{t-1}+u_{t}
$$

An equivalent representation is

$$
\nabla \boldsymbol{y}_{t}=\boldsymbol{c}+\Phi(\mathbf{B}) \nabla \boldsymbol{y}_{t-1}+\Pi \boldsymbol{y}_{t-1}+\boldsymbol{u}_{t}
$$

其中

$$
\Pi=\boldsymbol{A}-\boldsymbol{I}_{n}=-\boldsymbol{A}(1)
$$

## VECTOR AUTOREGRESSIONS WITH COINTEGRATED VARIABLES(协整向量自回归变量)

### note 2

A = I_n implies:
$$
|\boldsymbol{\Pi}|=\left|\boldsymbol{A}_{1}+\cdots+\boldsymbol{A}_{p}-\boldsymbol{I}_{n}\right|=0
$$

```
长期矩阵是奇异的，因此，它的秩必须小于n。
VAR包含至少一个单位根。但是，请注意上式并不一定意味着a=I_n，正是这个事实导致了协整VARs(CVARs)。
```

### note 3

Substitute
$$
\Pi=\boldsymbol{\beta} \boldsymbol{\alpha}^{\prime}
$$
into
$$
\nabla y_{t}=c+\Phi(B) \nabla y_{t-1}+\beta \alpha^{\prime} y_{t-1}+u_{t}
$$

### note 4

> ***vector error correction model (VECM):***

$$
\nabla \boldsymbol{y}_{t}=\boldsymbol{c}+\boldsymbol{\Phi}(B) \nabla \boldsymbol{y}_{t-1}+\beta \boldsymbol{e}_{t-1}+\boldsymbol{u}_{t}
$$

其中
$$
\boldsymbol{e}_{t}=\alpha^{\prime} \boldsymbol{y}_{\boldsymbol{t}}
$$
包含r平稳误差修正。



## ESTIMATION OF VECTOR ERROR CORRECTION MODELS AND TESTS OF COINTEGRATING RANK(矢量误差修正模型的估计和协整秩检验)

### note 5

VECM:
$$
\nabla \boldsymbol{y}_{t}=c+\sum_{i=1}^{p-1} \boldsymbol{\Phi}_{i} \nabla \boldsymbol{y}_{t-i}+\beta \boldsymbol{\alpha}^{\prime} \boldsymbol{y}_{t-1}+\boldsymbol{u}_{t}
$$
转为一个广义的特征值问题，并求解如下形式的一组方程:
$$
\left(\lambda_{i} \boldsymbol{S}_{11}-\boldsymbol{S}_{10} \boldsymbol{S}_{00}^{-1} \boldsymbol{S}_{01}\right) \boldsymbol{v}_{i}=0 \quad i=1, \ldots, n
$$
subject to:
$$
\boldsymbol{V} \boldsymbol{S}_{11} \boldsymbol{V}=\boldsymbol{I}_{n}
$$
α的ML估计由对应于r个最大特征值的特征向量给出:
$$
\hat{\alpha}=\left(v_{1}, v_{2}, \ldots, v_{r}\right)
$$

### note 6

VAR的水平:
$$
\boldsymbol{A}(B) \boldsymbol{y}_{t}=\boldsymbol{c}+\boldsymbol{d} t+\boldsymbol{u}_{t}
$$
intercept and trend coefficients may be written as:

$$
\boldsymbol{c}=\boldsymbol{\beta} \gamma_{1}+\boldsymbol{\beta}_{\perp} \gamma_{1}^{*} \quad \boldsymbol{d}=\boldsymbol{\beta} \boldsymbol{\gamma}_{2}+\boldsymbol{\beta}_{\perp} \boldsymbol{\gamma}_{2}^{*}
$$

follows that

$$
\boldsymbol{\beta}^{\prime} \boldsymbol{c}=\boldsymbol{\beta} \boldsymbol{\beta} \boldsymbol{\gamma}_{1}+\boldsymbol{\beta}^{\prime} \boldsymbol{\beta}_{\perp} \boldsymbol{\gamma}_{1}^{*}=\boldsymbol{\beta} \boldsymbol{\beta} \boldsymbol{\gamma}_{1}
$$

The associated VECM can then be written as

$$
\nabla \boldsymbol{y}_{t}=\Phi(B) \nabla \boldsymbol{y}_{t-1}+\boldsymbol{\beta}_{\perp}\left(\gamma_{1}^{*}+\gamma_{2}^{*} t\right)+\boldsymbol{\beta}\left(\gamma_{1}+\gamma_{2}(t-1)+\boldsymbol{e}_{t-1}\right)+\boldsymbol{u}_{t}
$$



## IDENTIFICATION OF VECTOR ERROR CORRECTION MODELS(矢量误差修正模型的辨识)

### note 7

> ***triangular representation:***

$$
\boldsymbol{\alpha}^{\prime}=\left[\begin{array}{ll}
\boldsymbol{I}_{r} & -\boldsymbol{\Gamma}
\end{array}\right]
$$

### note 8

> ***VECM (15.7) as the pair of “marginal” models:***

$$
\begin{aligned}
&\nabla \boldsymbol{x}_{t}=\boldsymbol{c}_{1}+\sum_{i=1}^{p-1} \boldsymbol{\Phi}_{1, i} \nabla \boldsymbol{y}_{t-i}+\boldsymbol{\beta}_{1} \boldsymbol{\alpha}^{\prime} \boldsymbol{y}_{t-1}+\boldsymbol{u}_{1, t} \\
&\nabla \boldsymbol{z}_{t}=\boldsymbol{c}_{2}+\sum_{i=1}^{p-1} \boldsymbol{\Phi}_{2, i} \nabla \boldsymbol{y}_{t-i}+\boldsymbol{\beta}_{2} \boldsymbol{\alpha}^{\prime} \boldsymbol{y}_{t-1}+\boldsymbol{u}_{2, t}
\end{aligned}
$$

其中

$$
\boldsymbol{\Phi}_{i}=\left[\begin{array}{l}
\boldsymbol{\Phi}_{1, i} \\
\boldsymbol{\Phi}_{2, i}
\end{array}\right] \quad i=1, \ldots, m-1 \quad \boldsymbol{\beta}=\left[\begin{array}{l}
\boldsymbol{\beta}_{1} \\
\boldsymbol{\beta}_{2}
\end{array}\right] \quad \boldsymbol{u}_{t}=\left[\begin{array}{l}
\boldsymbol{u}_{1, t} \\
\boldsymbol{u}_{2, t}
\end{array}\right]
$$



## STRUCTURAL VECTOR ERROR CORRECTION MODELS(结构向量误差修正模型)

### note 9

> ***a “structural VECM”:***

$$
\boldsymbol{\Gamma}_{0} \nabla \boldsymbol{y}_{t}=\sum_{i=1}^{p-1} \boldsymbol{\Gamma}_{i} \nabla \boldsymbol{y}_{t-i}+\Theta \boldsymbol{\alpha} \boldsymbol{y}_{t-1}+\boldsymbol{v}_{t}
$$

> ***“reduced form” VECM:***

$$
\nabla \boldsymbol{y}_{t}=\sum_{i=1}^{p-1} \boldsymbol{\Phi}_{i} \nabla \boldsymbol{y}_{t-i}+\boldsymbol{\beta} \boldsymbol{\alpha} \boldsymbol{y}_{t-1}+\boldsymbol{u}_{t}
$$

through

$$
\begin{gathered}
\boldsymbol{\Gamma}_{i}=\boldsymbol{\Gamma}_{0} \boldsymbol{\Phi}_{i} \quad i=1, \ldots, p-1 \\
\boldsymbol{\Gamma}_{0} \boldsymbol{\beta}=\boldsymbol{\Theta} \quad \boldsymbol{\nu}_{t}=\boldsymbol{\Gamma}_{0} \boldsymbol{u}_{t}
\end{gathered}
$$

so

$$
E\left(\boldsymbol{\nu}_{t} \boldsymbol{\nu}_{t}^{\prime}\right)=\boldsymbol{\Gamma}_{0} \boldsymbol{\Omega}_{p} \boldsymbol{\Gamma}_{0}^{\prime}
$$



## CAUSALITY TESTING IN VECTOR ERROR CORRECTION MODELS(向量误差修正中的因果检验模型)

### note 10

> ***a “fully partitioned” form of the marginal VECM:***



$$
\begin{aligned}
&\nabla \boldsymbol{x}_{t}=\boldsymbol{c}_{1}+\sum_{i=1}^{p-1} \boldsymbol{\Phi}_{11, i} \nabla \boldsymbol{x}_{t-i}+\sum_{i=1}^{p-1} \boldsymbol{\Phi}_{12, i} \nabla \boldsymbol{z}_{t-i}+\boldsymbol{\beta}_{1} \boldsymbol{\alpha}_{1}^{\prime} \boldsymbol{x}_{t-1}+\boldsymbol{\beta}_{1} \boldsymbol{\alpha}_{2}^{\prime} \boldsymbol{z}_{t-1}+\boldsymbol{u}_{1, t} \\
&\nabla z_{t}=\boldsymbol{c}_{2}+\sum_{i=1}^{p-1} \boldsymbol{\Phi}_{21, i} \nabla \boldsymbol{x}_{t-i}+\sum_{i=1}^{p-1} \boldsymbol{\Phi}_{22, i} \nabla \boldsymbol{z}_{t-i}+\boldsymbol{\beta}_{2} \boldsymbol{\alpha}_{1}^{\prime} \boldsymbol{x}_{t-1}+\boldsymbol{\beta}_{2} \boldsymbol{\alpha}_{2}^{\prime} \boldsymbol{z}_{t-1}+\boldsymbol{u}_{1, t}
\end{aligned}
$$

其中

$$
\boldsymbol{\Phi}_{i}=\left[\begin{array}{ll}
\boldsymbol{\Phi}_{11, i} & \boldsymbol{\Phi}_{12, i} \\
\boldsymbol{\Phi}_{21, i} & \boldsymbol{\Phi}_{22, i}
\end{array}\right] \quad \boldsymbol{\alpha}^{\prime}=\left[\begin{array}{ll}
\boldsymbol{\alpha}_{1} & \boldsymbol{\alpha}_{2}
\end{array}\right]^{\prime}
$$

> ***hypothesis:***

$$
\mathcal{H}_{0}: \boldsymbol{\Phi}_{12,1}=\cdots=\boldsymbol{\Phi}_{12, p-1}=\mathbf{0}, \quad \boldsymbol{\beta}_{1} \alpha_{2}^{\prime}=\mathbf{0}
$$

## IMPULSE RESPONSE ASYMPTOTICS(脉冲响应渐近) IN NONSTATIONARY VARs

### note 11

the various impulse responses of the VAR are computed from the sequence of matrices:
$$
\boldsymbol{\Psi}_{i}=\sum_{j=1}^{i} \boldsymbol{A}_{j} \boldsymbol{\Psi}_{i-j}, \quad \boldsymbol{\Psi}_{0}=\boldsymbol{I}_{n} \quad \boldsymbol{\Psi}_{i}=\mathbf{0}, \quad i<0
$$

```
在平稳var中，长期矩阵Π的所有根小于1，估计的脉冲响应可能显示为一致和渐近正态，Ψ_i和他们的估计Ψ_i趋于零。对于非平稳var，Ψ_i不一定会消亡为i-N，一个不同的极限理论为脉冲响应估计。
```

```
注：
由于知道系统中单位根的数量对于获得准确的估计是必要的，所以重要的是协整秩的选择是通过一个一致的方法
```



## VECTOR ERROR CORRECTION MODEL-X MODELS(矢量误差修正模型- x模型)

### note 12

> ***extension of the CVAR/VECM model:***

$$
\nabla \boldsymbol{y}_{t}=\boldsymbol{c}+\boldsymbol{d} t+\sum_{i=1}^{p-1} \boldsymbol{\Phi}_{i} \nabla \boldsymbol{y}_{t-i}+\boldsymbol{\beta} \boldsymbol{\alpha} \boldsymbol{y}_{t-1}+\boldsymbol{\Lambda} \boldsymbol{w}_{t}+\boldsymbol{u}_{t}
$$

```
注：
协整秩的估计和检验与以前完全相同，但检验的临界值可能会受到影响。
```



## COMMON TRENDS AND CYCLES(常见趋势和周期)

### note 13

> ***CVAR中存在线性趋势:***

$$
\boldsymbol{C}(B) \Pi(B)=\nabla \boldsymbol{I}_{n}
$$

有：
$$
\begin{aligned}
\boldsymbol{C}(B) &=\boldsymbol{I}_{n}+\boldsymbol{C} B+\left(\boldsymbol{C}_{1}^{*} B+\boldsymbol{C}_{2}^{*} B^{2}+\cdots\right) \nabla \\
&=\boldsymbol{I}_{n}+\boldsymbol{C}+\left(\boldsymbol{C}_{0}^{*}+\boldsymbol{C}_{1}^{*} B+\boldsymbol{C}_{2}^{*} B^{2}+\cdots\right) \nabla \\
&=\boldsymbol{I}_{n}+\boldsymbol{C}+\boldsymbol{C}^{*}(B) \nabla \\
&=\boldsymbol{C}(1)+\boldsymbol{C}^{*}(B) \nabla
\end{aligned}
$$
其中



$$
\boldsymbol{C}_{i}=\sum_{j=1}^{p} \boldsymbol{C}_{i-j} \boldsymbol{A}_{j}, \quad i>0, \quad \boldsymbol{C}_{0}=\boldsymbol{I}_{n}
$$

so

$$
\boldsymbol{C}=\sum_{i=1}^{\infty} \boldsymbol{C}_{i}=\boldsymbol{C}(1)-\boldsymbol{I}_{n}
$$

follows that

$$
C_{0}^{*}=-C
$$

and

$$
\boldsymbol{C}_{i}^{*}=\boldsymbol{C}_{i-1}^{*}+\boldsymbol{C}_{i}, \quad i>0
$$

written as

$$
\begin{aligned}
\nabla \boldsymbol{y}_{t} &=\boldsymbol{C}(B)\left(\boldsymbol{c}+\boldsymbol{d} t+\boldsymbol{u}_{t}\right) \\
&=\left(\boldsymbol{C}(1)+\boldsymbol{C}^{*}(B) \nabla\right)(\boldsymbol{c}+\boldsymbol{d} t)+\boldsymbol{C}(B) \boldsymbol{u}_{t} \\
&=\boldsymbol{C}(1) \boldsymbol{c}+\boldsymbol{C}^{*}(1) \boldsymbol{d}+\boldsymbol{C}(1) \boldsymbol{d} t+\boldsymbol{C}(B) \boldsymbol{u}_{t} \\
&=\boldsymbol{b}_{0}+\boldsymbol{b}_{1} t+\boldsymbol{C}(B) \boldsymbol{u}_{t}
\end{aligned}
$$

其中

$$
\boldsymbol{b}_{0}=\boldsymbol{C}(1) \boldsymbol{c} \quad \boldsymbol{b}_{1}=\boldsymbol{C}(1) \boldsymbol{d}
$$

becomes:

$$
\begin{aligned}
\boldsymbol{y}_{t} &=\boldsymbol{y}_{0}+\boldsymbol{b}_{0} t+\boldsymbol{b}_{1} \frac{t(t+1)}{2}+\boldsymbol{C}(B) \sum_{s=1}^{t} \boldsymbol{u}_{t} \\
&=\boldsymbol{y}_{0}+\boldsymbol{b}_{0} t+\boldsymbol{b}_{1} \frac{t(t+1)}{2}+\left(\boldsymbol{C}(1)+\boldsymbol{C}^{*} \nabla\right) \sum_{s=1}^{t} \boldsymbol{u}_{t} \\
&=\boldsymbol{y}_{0}+\boldsymbol{b}_{0} t+\boldsymbol{b}_{1} \frac{t(t+1)}{2}+\boldsymbol{C}(1) \boldsymbol{s}_{t}+\boldsymbol{C}^{*}(B)\left(\boldsymbol{u}_{t}-\boldsymbol{u}_{0}\right) \\
&=\boldsymbol{y}_{0}^{*}+\boldsymbol{b}_{0} t+\boldsymbol{b}_{1} \frac{t(t+1)}{2}+\boldsymbol{C}(1) \boldsymbol{s}_{t}+\boldsymbol{C}^{*}(B) \boldsymbol{u}_{t}
\end{aligned}
$$

其中

$$
\boldsymbol{y}_{0}^{*}=\boldsymbol{y}_{0}-\boldsymbol{C}^{*}(B) \boldsymbol{u}_{0}, \quad \boldsymbol{s}_{t}=\sum_{s=1}^{t} \boldsymbol{u}_{s}
$$

当b1 = 0,y0 = u0 = 0时:
$$
\boldsymbol{y}_{t}=\boldsymbol{b}_{0}+\boldsymbol{C}(1) \boldsymbol{s}_{t}+\boldsymbol{C}^{*}(B) \boldsymbol{u}_{t}=\boldsymbol{C}(1)\left(\boldsymbol{c}+\boldsymbol{s}_{t}\right)+\boldsymbol{C}^{*}(B) \boldsymbol{u}_{t}
$$
On defining

$$
\tau_{t}=\boldsymbol{\delta}^{\prime}\left(c+s_{t}\right) \quad c_{t}=C^{*}(B) u_{t}
$$

> ***“common trends” representation:***

$$
\begin{gathered}
y_{t}=\rho \tau_{t}+c_{t} \\
\tau_{t}=\tau_{t-1}+\delta^{\prime} u_{t}
\end{gathered}
$$



### note 14

> ***common trend-common cycle representation:***

$$
\boldsymbol{y}_{t}=\rho \tau_{t}+\boldsymbol{G} \tilde{c}_{t}
$$

$$
\left[\begin{array}{cc}
\boldsymbol{I}_{s} & \phi^{* \prime} \\
\mathbf{0}_{(n-s) \times s} & \boldsymbol{I}_{n-s}
\end{array}\right] \nabla \boldsymbol{y}_{t}=\left[\begin{array}{c}
\mathbf{0}_{s \times(n(p-1)+r)} \\
\boldsymbol{\Phi}_{1}^{*}, \ldots, \boldsymbol{\Phi}_{p-1}^{*} \boldsymbol{\beta}^{*}
\end{array}\right]\left[\begin{array}{c}
\nabla \boldsymbol{y}_{t-1} \\
\vdots \\
\nabla \boldsymbol{y}_{t-p+1} \\
\boldsymbol{e}_{t-1}
\end{array}\right]+\boldsymbol{u}_{t}
$$

```
注：
该系统可以用全信息极大似然估计或其他联立方程估计技术来估计。然后可以构造s共特征向量施加的限制的似然比统计量，该统计量将以χ2的形式渐近分布，其自由度由施加的限制数量给出。
```

