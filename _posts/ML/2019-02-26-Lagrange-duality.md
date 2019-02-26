---
layout: post
title: 拉格朗日对偶性
category: ML
keywords: 拉格朗日，对偶性
---

# 拉格朗日对偶性
将约束最优化问题（原始问题）

$$\min_{x} f(x)\tag{C.1}$$
$$s.t. \qquad c_i(x) \le 0, \ i=1,2,...,k\tag{C.2}$$
$$ \qquad \ \ \ \ \ \ h_j(x) = 0, \ j=1,2,...,l \tag{C.3}$$
表示成广义拉格朗日函数的极小极大问题：
$$\min_{x}\max_{\alpha, \beta; \alpha_{i}\ge0} \mathcal{L}(x,\alpha, \beta) \tag{C.6}$$
$$\theta_{p} = \max_{\alpha, \beta; \alpha_{i}\ge0}\mathcal{L}(x,\alpha, \beta) \tag{C.5}$$
$$\mathcal{L}(x,\alpha, \beta) = f(x) + \sum_{i=1}^{k}\alpha_{i}c_{i}(x) + \sum_{j=1}^{l}\beta_{j}h_{j}(x)\tag{C.4}$$

进而有广义拉格朗日函数的极大极小问题:
$$\max_{\alpha, \beta; \alpha_{i}\ge0}\min_{x} \mathcal{L}(x,\alpha, \beta) \tag{C.8}$$
$$\theta_{d}(\alpha,\beta) = \min_{x}\mathcal{L}(x,\alpha, \beta) \tag{C.7}$$
将其表示成约束最优化问题就是原始问题的对偶问题：
$$\max_{\alpha,\beta}\theta_{d}(\alpha,\beta)=\max_{\alpha, \beta}\min_{x} \mathcal{L}(x,\alpha, \beta) \tag{C.9}$$
$$s.t. \qquad \alpha_{i}\ge 0, i=1,2,...,k$$

当满足一定条件时，可用解原始问题来解对偶问题。即当原始问题与对偶问题的最优值（最优值不是最优解）都存在且相等时。

当原始问题与对偶问题都有最优值时，有原始问题的最优值（$p^{*}$）大于等于对偶问题的最优值（$d^*$）。（见定理C.1）

而何时原始问题与对偶问题的相等呢? 这时就用到了定理C.2和定理C.3 KKT条件。

**定理C.2**

假设函数$f(x)$与不等式约束条件$c_{i}(x)$是凸函数，等式约束条件$h_{j}$是仿射函数，并且不等式约束$c_{i}(x)$是严格可行的，即存在$x$，对所有$i$有$c_{i}(x)\le0$，则存在$x^{*}, \alpha^{*}, \beta^{*}$，使$x^{*}$是原始问题的解，$\alpha^{*}, \beta^{*}$是对偶问题的解，并且有:
$$p^{*}=d^{*}=\mathcal{L}(x,\alpha,\beta)\tag{C.10}$$

在求解过程中用到**定理C.3**的**KKT条件**建立方程组：$x^{*}, \alpha^{*}, \beta^{*}$分别是原始问题和对偶问题的解的充分必要条件是满足$x^{*}, \alpha^{*}, \beta^{*}$满足下面的 **Karush-Kuhn-Tucker(KKT)** 条件：

首先对拉格朗日函数对各个参数求偏导等于0：
$$\nabla_{x}\mathcal{L}(x,\alpha,\beta)=0$$
$$\nabla_{\alpha}\mathcal{L}(x,\alpha,\beta)=0$$
$$\nabla_{\beta}\mathcal{L}(x,\alpha,\beta)=0$$

还需要同时满足等式约束条件与不等式约束条件：
$$c_i(x) \le 0, i=1,2,...,k$$
$$h_j(x) = 0, j=1,2,...,l$$

还需要对不等式约束条件的拉格朗日乘子进行约束
$$\alpha^{i} \ge 0, i=1,2,...,k$$
$$\alpha^{i}c_{i}(x^{*})=0, i=1,2,...,k$$ 
最后一个$\alpha^{i}c_{i}(x^{*})=0, i=1,2,...,k$ **KKT条件的互补条件**， 由此条件可知：若$\alpha^{i}\ge 0$ 则 $c_{i}=0$
