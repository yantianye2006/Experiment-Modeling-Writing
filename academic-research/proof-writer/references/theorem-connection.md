# 定理连结方法

本文件说明如何从已知定理推导新结果、常用定理清单（按领域分类），以及引用和连结
定理的规范。

---

## 定理连结的基本思路

### 什么是定理连结？

定理连结是指在证明新结果时，识别并利用已有的定理作为中间步骤或基础工具。一个好
的证明通常是「站在巨人的肩膀上」——善用已知结果，只推导真正新的部分。

### 连结流程

1. **分解主张**：将要证明的主张分解为多个子问题。
2. **匹配已知结果**：对每个子问题，搜索可用的已知定理。
3. **验证前提**：确认已知定理的前提条件在当前语境下成立。
4. **填补空隙**：对已知定理无法覆盖的部分，进行原创推导。
5. **组合结果**：将所有部分组合成完整的证明。

### 连结策略

#### 策略一：直接引用

最简单的连结方式。当已知定理可以直接应用时：

```latex
By Theorem~\ref{thm:known-result}, we have [conclusion].
```

**前提**：已知定理的所有前提条件在当前语境下都满足。

#### 策略二：特化 (Specialization)

将一般性定理应用到特殊情况：

```latex
Applying Theorem~\ref{thm:general} with $X = [specific choice]$
and $Y = [specific choice]$, we obtain [specific conclusion].
```

**适用**：当已知定理比需要的更一般时。

#### 策略三：推广 (Generalization)

证明已知定理的推广版本。通常需要修改原始证明：

```latex
The proof follows the same strategy as [Reference], with the
following modifications: ...
```

**适用**：当已知定理几乎但不完全适用时。

#### 策略四：组合 (Combination)

将多个定理的结论组合起来：

```latex
Combining Lemma~\ref{lem:A} and Lemma~\ref{lem:B}, we obtain ...
```

**适用**：当没有单一定理足以完成证明，但多个定理的结合可以时。

#### 策略五：链式推导 (Chaining)

将多个定理串联成推导链：

```latex
By Theorem A, we have [result 1]. Applying Theorem B to [result 1],
we obtain [result 2]. Finally, Theorem C yields [conclusion].
```

**适用**：证明需要经过多个中间步骤时。

---

## 常用定理清单

### 分析 (Analysis)

| 定理 | 陈述摘要 | 常见用途 |
|------|---------|---------|
| Cauchy-Schwarz inequality | $|\langle x, y \rangle| \leq \|x\| \cdot \|y\|$ | 内积估计、上界推导 |
| Triangle inequality | $\|x + y\| \leq \|x\| + \|y\|$ | 距离估计 |
| Jensen's inequality | $f(\mathbb{E}[X]) \leq \mathbb{E}[f(X)]$ for convex $f$ | 凸函数、期望值界 |
| Hölder's inequality | $\|fg\|_1 \leq \|f\|_p \|g\|_q$ where $1/p+1/q=1$ | $L^p$ 空间估计 |
| Minkowski's inequality | $\|f+g\|_p \leq \|f\|_p + \|g\|_p$ | 范数的三角不等式 |
| Mean Value Theorem | $f(b)-f(a) = f'(c)(b-a)$ | 差值估计 |
| Taylor's theorem | $f(x) = \sum_{k=0}^n \frac{f^{(k)}(a)}{k!}(x-a)^k + R_n$ | 近似与误差界 |
| Dominated Convergence | 控制收敛定理 | 交换极限与积分 |
| Monotone Convergence | 单调收敛定理 | 非负函数序列积分 |

### 机率论 (Probability Theory)

| 定理 | 陈述摘要 | 常见用途 |
|------|---------|---------|
| Markov's inequality | $\Pr[X \geq a] \leq \mathbb{E}[X]/a$ | 基本尾界 |
| Chebyshev's inequality | $\Pr[|X-\mu| \geq k\sigma] \leq 1/k^2$ | 方差尾界 |
| Hoeffding's inequality | 有界随机变数和的集中不等式 | 有限样本界 |
| Bernstein's inequality | 考虑方差的集中不等式 | 更紧的集中界 |
| Chernoff bound | 矩生成函数尾界 | 指数型集中 |
| Central Limit Theorem | $\bar{X}_n \xrightarrow{d} N(\mu, \sigma^2/n)$ | 渐近分析 |
| Law of Large Numbers | $\bar{X}_n \xrightarrow{a.s.} \mu$ | 一致性证明 |
| Borel-Cantelli lemma | 事件发生无限次的条件 | 几乎必然收敛 |
| Union bound | $\Pr[\bigcup A_i] \leq \sum \Pr[A_i]$ | 多事件机率上界 |
| McDiarmid's inequality | 有界差分函数的集中 | 函数集中不等式 |

### 线性代数 (Linear Algebra)

| 定理 | 陈述摘要 | 常见用途 |
|------|---------|---------|
| Spectral theorem | 对称矩阵的正交分解 | 矩阵分析 |
| Singular Value Decomposition | $A = U\Sigma V^T$ | 矩阵近似、降维 |
| Rank-nullity theorem | $\mathrm{rank}(A) + \mathrm{null}(A) = n$ | 线性系统分析 |
| Perron-Frobenius theorem | 非负矩阵的主特征值 | 马可夫链 |
| Matrix inversion lemma | $(A + UCV)^{-1}$ 的展开 | 高效计算 |
| Courant-Fischer theorem | 特征值的 min-max 表示 | 特征值界 |
| Weyl's inequality | 特征值扰动界 | 扰动分析 |

### 最佳化 (Optimization)

| 定理 | 陈述摘要 | 常见用途 |
|------|---------|---------|
| KKT conditions | 凸最佳化的最优性条件 | 最优解刻画 |
| Strong duality | 凸问题的零对偶间隙 | 对偶方法 |
| Gradient descent convergence | 凸且 Lipschitz 梯度下的收敛率 | 演算法分析 |
| Minimax theorem | $\min_x \max_y = \max_y \min_x$ (凸-凹) | 对抗训练、博弈论 |
| Projection theorem | 闭凸集上的最近点唯一存在 | 凸约束问题 |
| Slater's condition | 强对偶性的充分条件 | 验证强对偶 |

### 机器学习理论 (Learning Theory)

| 定理 | 陈述摘要 | 常见用途 |
|------|---------|---------|
| VC dimension bound | $\epsilon$-net 与 VC 维的样本界 | 泛化界 |
| Rademacher complexity bound | 基于 Rademacher 复杂度的泛化界 | 泛化分析 |
| PAC-Bayes bound | 后验加权假设的泛化界 | 贝式学习 |
| No Free Lunch theorem | 无通用最优演算法 | 理论限制 |
| Bias-variance decomposition | 期望误差分解 | 模型选择 |
| Fano's inequality | 互资讯与错误率的关系 | minimax 下界 |
| Le Cam's method | 两假设测试下界 | 估计下界 |
| Assouad's lemma | 多假设测试下界 | 高维估计下界 |

### 资讯论 (Information Theory)

| 定理 | 陈述摘要 | 常见用途 |
|------|---------|---------|
| Shannon's source coding | 无损压缩的极限为 $H(X)$ | 压缩界 |
| Channel coding theorem | 通讯率可达 $C = \max I(X;Y)$ | 容量界 |
| Data processing inequality | $I(X;Z) \leq I(X;Y)$ for $X \to Y \to Z$ | 资讯损失 |
| Entropy power inequality | $N(X+Y) \geq N(X) + N(Y)$ | 容量界 |
| Mrs. Gerber's lemma | BSC 组合的熵界 | 二元通道 |
| Pinsker's inequality | TV 距离与 KL 散度的关系 | 分布距离 |
| Gibbs' inequality | $D_{\mathrm{KL}}(P \| Q) \geq 0$ | KL 非负性 |

---

## 引用与连结规范

### 引用格式

#### 引用论文自身的结果

```latex
% 引用同一篇论文中的定理
By Theorem~\ref{thm:our-main-result}, ...
As shown in Lemma~\ref{lem:auxiliary}, ...
From Equation~\eqref{eq:key-bound}, ...
```

#### 引用外部文献

```latex
% 引用其他论文的结果
By \cite[Theorem~3.2]{author2024paper}, ...
Following the approach of \cite{author2023}, ...
Using the result of \citet{author2022} (specifically, their Theorem~5), ...
```

#### 引用经典结果

```latex
% 众所周知的结果可不引用具体文献
By the Cauchy-Schwarz inequality, ...
By Jensen's inequality, ...
% 但较不常见的结果应提供引用
By the Lovász Local Lemma (see, e.g., \cite[Chapter~5]{alon2016book}), ...
```

### 引用的完整性原则

1. **自明结果**：众所周知的基本定理（如 Cauchy-Schwarz）可不附引用。
2. **标准结果**：领域内广为人知的结果，附上经典教科书引用。
3. **近期结果**：近年发表的结果，必须附上原始论文引用。
4. **本文结果**：引用本文前面已证明的引理或命题。

### 连结的视觉化

在复杂的证明中，建议在证明开始前提供推导结构的概览：

```latex
\begin{remark}[Proof outline]
  The proof proceeds in three steps. First, we establish [A]
  using Lemma~\ref{lem:step1}. Then, combining [A] with
  Theorem~\ref{thm:known}, we derive [B]. Finally, we apply
  [B] to obtain the main result.
\end{remark}
```

### 定理依赖图

对于包含多个引理和定理的论文，维护一个心理上的（或实际的）依赖图：

```
Lemma 1 ──┐
           ├──→ Theorem 1 ──┐
Lemma 2 ──┘                 │
                             ├──→ Main Theorem
Lemma 3 ──→ Theorem 2 ──────┘
```

确保依赖关系是有向无环的 (DAG)，且陈述顺序与依赖顺序一致。
