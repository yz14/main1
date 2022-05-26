---
sort: 1
---

# 梯度方法

$f(x) = x^2$

优化问题常常是寻找一个函数$ f(x), x\in \Omega $的最大或最小值以及其对应的最优解$x^+$。
对于简单的函数，例如二次函数，我们可以直接找到其最优解，即，令$\frac{\partial f(x)}{\partial x} = 0$。
然而，对于非常复杂的函数，我们无法通过一次计算得到最优解，这时，我们可以选取一个点，然后通过逐步的搜索来找到最优解。
我们可以朝着让函数值减小的方向一直进行搜索，由于某一点的梯度方向代表函数在该点变化速率最快的方向，于是，
我们可以用梯度方法很快地找到最优解：

$$\begin{align}
x_{t+1} = x_t - \eta_t \nabla f(x_t)^T
\end{align}$$

如果$x_{t+1} \notin \Omega$，我们可以先将其投影到$\Omega$上：
\begin{align}
    y_{t+1} &= x_t - \eta_t \nabla f(x_t)^T \\
    x_{t+1} &= \Pi_{\Omega}(y_{t+1})
\end{align}

其中$\Pi_{\Omega}(y) = \mathop{\arg\min}_{x \in \Omega}\|x-y\|$是投影操作。
由separation theorem可知，$(\Pi_{\Omega}(y)-x)^T(\Pi_{\Omega}(y)-y) \leq 0$，于是：
\begin{align}
    2(\Pi_{\Omega}(y)-x)^T(\Pi_{\Omega}(y)-y) &= \|\Pi_{\Omega}(y)-x\|^2 + 
    \|\Pi_{\Omega}(y)-y\|^2 - \|x-y\|^2 \\
    \Rightarrow \|\Pi_{\Omega}(y)-x\|^2 &\leq \|x-y\|^2 - \|\Pi_{\Omega}(y)-y\|^2
\end{align}
