# 数学符号惯例

本文件统整数学符号的使用惯例，涵盖一般数学、机器学习/深度学习领域常用符号，
以及符号一致性原则和常见冲突的解决方法。

---

## 一般数学符号

### 集合与空间

| 符号 | 含义 | LaTeX |
|------|------|-------|
| $\mathbb{R}$ | 实数集 | `\mathbb{R}` |
| $\mathbb{R}^n$ | $n$ 维实数空间 | `\mathbb{R}^n` |
| $\mathbb{R}^{m \times n}$ | $m \times n$ 实数矩阵空间 | `\mathbb{R}^{m \times n}` |
| $\mathbb{Z}$ | 整数集 | `\mathbb{Z}` |
| $\mathbb{N}$ | 自然数集 | `\mathbb{N}` |
| $\mathbb{C}$ | 复数集 | `\mathbb{C}` |
| $\mathbb{Q}$ | 有理数集 | `\mathbb{Q}` |
| $\emptyset$ | 空集 | `\emptyset` |
| $\mathcal{X}$ | 输入空间 | `\mathcal{X}` |
| $\mathcal{Y}$ | 输出空间 | `\mathcal{Y}` |
| $\mathcal{H}$ | 假设类 / Hilbert space | `\mathcal{H}` |
| $\mathcal{F}$ | 函数类 | `\mathcal{F}` |
| $\mathbb{S}^n$ | $n$ 维球面 | `\mathbb{S}^n` |
| $\Delta_n$ | $n$ 维单纯形 | `\Delta_n` |

### 集合运算

| 符号 | 含义 | LaTeX |
|------|------|-------|
| $\in$ | 属于 | `\in` |
| $\notin$ | 不属于 | `\notin` |
| $\subseteq$ | 子集（含等号） | `\subseteq` |
| $\subset$ | 真子集 | `\subset` |
| $\cup$ | 联集 | `\cup` |
| $\cap$ | 交集 | `\cap` |
| $\setminus$ | 集合差 | `\setminus` |
| $\times$ | 笛卡尔积 | `\times` |
| $|A|$ | 集合大小 | `|A|` or `\lvert A \rvert` |

### 逻辑符号

| 符号 | 含义 | LaTeX |
|------|------|-------|
| $\forall$ | 对所有 | `\forall` |
| $\exists$ | 存在 | `\exists` |
| $\nexists$ | 不存在 | `\nexists` |
| $\Rightarrow$ | 蕴涵 | `\Rightarrow` |
| $\Leftrightarrow$ | 若且唯若 | `\Leftrightarrow` |
| $\neg$ | 否定 | `\neg` |
| $\wedge$ | 且 | `\wedge` |
| $\vee$ | 或 | `\vee` |

### 函数与运算

| 符号 | 含义 | LaTeX |
|------|------|-------|
| $f: A \to B$ | 函数映射 | `f: A \to B` |
| $f \circ g$ | 函数合成 | `f \circ g` |
| $f^{-1}$ | 反函数 | `f^{-1}` |
| $\sup$ | 上确界 | `\sup` |
| $\inf$ | 下确界 | `\inf` |
| $\max$ | 最大值 | `\max` |
| $\min$ | 最小值 | `\min` |
| $\arg\max$ | 取最大值的引数 | `\arg\max` or `\operatorname{argmax}` |
| $\arg\min$ | 取最小值的引数 | `\arg\min` or `\operatorname{argmin}` |
| $\lim$ | 极限 | `\lim` |
| $O(\cdot)$ | 大 O 记号 | `O(\cdot)` |
| $\Omega(\cdot)$ | 大 Omega 记号 | `\Omega(\cdot)` |
| $\Theta(\cdot)$ | 大 Theta 记号 | `\Theta(\cdot)` |
| $o(\cdot)$ | 小 o 记号 | `o(\cdot)` |

---

## 线性代数符号

### 向量与矩阵

| 符号 | 含义 | LaTeX | 备注 |
|------|------|-------|------|
| $\mathbf{x}$, $\boldsymbol{x}$ | 向量 | `\mathbf{x}`, `\boldsymbol{x}` | 粗体小写 |
| $\mathbf{A}$, $\boldsymbol{A}$ | 矩阵 | `\mathbf{A}`, `\boldsymbol{A}` | 粗体大写 |
| $\mathbf{I}$ | 单位矩阵 | `\mathbf{I}` | 有时记为 $I_n$ |
| $\mathbf{0}$ | 零向量/矩阵 | `\mathbf{0}` | 由语境判断 |
| $\mathbf{1}$ | 全一向量 | `\mathbf{1}` | |
| $\mathbf{e}_i$ | 第 $i$ 个标准基向量 | `\mathbf{e}_i` | |

### 矩阵运算

| 符号 | 含义 | LaTeX |
|------|------|-------|
| $A^T$ | 转置 | `A^T` or `A^\top` |
| $A^{-1}$ | 逆矩阵 | `A^{-1}` |
| $A^\dagger$ | 伪逆 | `A^\dagger` |
| $\mathrm{tr}(A)$ | 迹 | `\mathrm{tr}(A)` or `\operatorname{tr}(A)` |
| $\det(A)$ | 行列式 | `\det(A)` |
| $\mathrm{rank}(A)$ | 秩 | `\mathrm{rank}(A)` |
| $\lambda_i(A)$ | 第 $i$ 个特征值 | `\lambda_i(A)` |
| $\sigma_i(A)$ | 第 $i$ 个奇异值 | `\sigma_i(A)` |
| $A \succeq 0$ | 正半定 | `A \succeq 0` |
| $A \succ 0$ | 正定 | `A \succ 0` |
| $A \otimes B$ | Kronecker 积 | `A \otimes B` |
| $A \odot B$ | Hadamard (逐元素) 积 | `A \odot B` |

### 范数

| 符号 | 含义 | LaTeX |
|------|------|-------|
| $\|x\|$ | 范数（预设为 $\ell_2$） | `\|x\|` or `\lVert x \rVert` |
| $\|x\|_p$ | $\ell_p$ 范数 | `\|x\|_p` |
| $\|x\|_1$ | $\ell_1$ 范数 | `\|x\|_1` |
| $\|x\|_\infty$ | $\ell_\infty$ 范数 | `\|x\|_\infty` |
| $\|A\|_F$ | Frobenius 范数 | `\|A\|_F` |
| $\|A\|_{\mathrm{op}}$ | 运算元范数 | `\|A\|_{\mathrm{op}}` |
| $\|A\|_*$ | 核范数 | `\|A\|_*` |

### 内积

| 符号 | 含义 | LaTeX |
|------|------|-------|
| $\langle x, y \rangle$ | 内积 | `\langle x, y \rangle` |
| $x^T y$ | 向量点积 | `x^T y` |
| $x \cdot y$ | 点积（较少用） | `x \cdot y` |

---

## 机率与统计符号

### 基本机率

| 符号 | 含义 | LaTeX |
|------|------|-------|
| $\Pr[\cdot]$ | 机率 | `\Pr[\cdot]` |
| $\mathbb{E}[\cdot]$ | 期望值 | `\mathbb{E}[\cdot]` |
| $\mathrm{Var}[\cdot]$ | 变异数 | `\mathrm{Var}[\cdot]` |
| $\mathrm{Cov}[\cdot]$ | 共变异数 | `\mathrm{Cov}[\cdot]` |
| $X \sim P$ | $X$ 服从分布 $P$ | `X \sim P` |
| $X \perp Y$ | $X$ 与 $Y$ 独立 | `X \perp Y` |
| $X \mid Y$ | 条件于 $Y$ | `X \mid Y` |
| $\mathbb{E}[X \mid Y]$ | 条件期望 | `\mathbb{E}[X \mid Y]` |
| $p(x)$ | 机率密度/质量函数 | `p(x)` |
| $F(x)$ | 累积分布函数 | `F(x)` |
| $X_1, \ldots, X_n \overset{\text{i.i.d.}}{\sim} P$ | 独立同分布 | `\overset{\text{i.i.d.}}{\sim}` |

### 常见分布

| 符号 | 含义 | LaTeX |
|------|------|-------|
| $\mathcal{N}(\mu, \sigma^2)$ | 常态分布 | `\mathcal{N}(\mu, \sigma^2)` |
| $\mathrm{Bernoulli}(p)$ | 伯努利分布 | `\mathrm{Bernoulli}(p)` |
| $\mathrm{Uniform}(a, b)$ | 均匀分布 | `\mathrm{Uniform}(a, b)` |
| $\mathrm{Binomial}(n, p)$ | 二项分布 | `\mathrm{Binomial}(n, p)` |
| $\mathrm{Poisson}(\lambda)$ | 泊松分布 | `\mathrm{Poisson}(\lambda)` |
| $\mathrm{Exp}(\lambda)$ | 指数分布 | `\mathrm{Exp}(\lambda)` |

### 收敛记号

| 符号 | 含义 | LaTeX |
|------|------|-------|
| $\xrightarrow{d}$ | 分布收敛 | `\xrightarrow{d}` |
| $\xrightarrow{p}$ | 机率收敛 | `\xrightarrow{p}` |
| $\xrightarrow{a.s.}$ | 几乎必然收敛 | `\xrightarrow{a.s.}` |
| $\xrightarrow{L^p}$ | $L^p$ 收敛 | `\xrightarrow{L^p}` |

---

## ML/DL 领域常用符号

### 监督学习

| 符号 | 含义 | 备注 |
|------|------|------|
| $\mathcal{D}$ | 数据分布 | |
| $S = \{(x_i, y_i)\}_{i=1}^n$ | 训练集 | $n$ 个样本 |
| $f_\theta$ 或 $h_\theta$ | 参数化模型 | $\theta$ 为参数 |
| $\ell(\hat{y}, y)$ | 损失函数 | |
| $\mathcal{L}(\theta)$ | 经验损失 | $\frac{1}{n}\sum_i \ell(f_\theta(x_i), y_i)$ |
| $R(f)$ | 真实风险 | $\mathbb{E}_{(x,y)\sim\mathcal{D}}[\ell(f(x), y)]$ |
| $\hat{R}_n(f)$ | 经验风险 | |
| $\lambda$ | 正则化参数 | |
| $\Omega(\theta)$ | 正则化项 | |

### 深度学习

| 符号 | 含义 | 备注 |
|------|------|------|
| $W^{(l)}$ | 第 $l$ 层的权重矩阵 | |
| $b^{(l)}$ | 第 $l$ 层的偏差向量 | |
| $a^{(l)}$ | 第 $l$ 层的激活值 | |
| $\sigma(\cdot)$ | 激活函数 | ReLU, sigmoid 等 |
| $\nabla_\theta \mathcal{L}$ | 损失对参数的梯度 | |
| $\eta$ | 学习率 | |
| $B$ | batch size | |
| $T$ | 总训练步数或时间步 | |
| $L$ | 网路层数 | |
| $d$ | 特征维度 | |
| $d_{\mathrm{model}}$ | 模型维度 (Transformer) | |
| $d_k$, $d_v$ | key/value 维度 | |
| $h$ | 注意力头数 | |

### 最佳化

| 符号 | 含义 | 备注 |
|------|------|------|
| $\nabla f$ | 梯度 | |
| $\nabla^2 f$ | Hessian 矩阵 | |
| $\theta_{t+1} = \theta_t - \eta \nabla \mathcal{L}(\theta_t)$ | 梯度下降更新 | |
| $\beta_1, \beta_2$ | Adam 的动量参数 | |
| $\epsilon$ | 数值稳定性常数 | Adam 中 |
| $L$ | Lipschitz 常数 | 梯度 Lipschitz |
| $\mu$ | 强凸参数 | |
| $\kappa = L/\mu$ | 条件数 | |

### 资讯论 (ML 语境)

| 符号 | 含义 | LaTeX |
|------|------|-------|
| $H(X)$ | Shannon 熵 | `H(X)` |
| $H(X \mid Y)$ | 条件熵 | `H(X \mid Y)` |
| $I(X; Y)$ | 互资讯 | `I(X; Y)` |
| $D_{\mathrm{KL}}(P \| Q)$ | KL 散度 | `D_{\mathrm{KL}}(P \| Q)` |
| $h(X)$ | 微分熵 | `h(X)` |
| $\|P - Q\|_{\mathrm{TV}}$ | 全变差距离 | `\|P - Q\|_{\mathrm{TV}}` |

### 生成模型

| 符号 | 含义 | 备注 |
|------|------|------|
| $p_\theta(x)$ | 模型分布 | |
| $p_{\mathrm{data}}(x)$ | 真实数据分布 | |
| $q_\phi(z \mid x)$ | 编码器 (VAE) | |
| $p_\theta(x \mid z)$ | 解码器 (VAE) | |
| $z$ | 潜在变数 | |
| $\mathrm{ELBO}$ | 证据下界 | |
| $G$, $D$ | 生成器、判别器 (GAN) | |

---

## 符号一致性原则

### 原则一：全文一致

同一符号在整篇论文中必须代表同一含义。不同的概念必须使用不同的符号。

**错误范例**：在第 3 节用 $n$ 表示样本数，在第 5 节用 $n$ 表示维度。

**正确做法**：用 $n$ 表示样本数，$d$ 表示维度。

### 原则二：先定义后使用

每个符号在首次使用时必须明确定义。定义应出现在使用之前。

```latex
Let $n$ denote the number of training samples and $d$ denote the
input dimension. We consider a dataset
$S = \{(\mathbf{x}_i, y_i)\}_{i=1}^n$ where
$\mathbf{x}_i \in \mathbb{R}^d$.
```

### 原则三：遵循领域惯例

优先使用领域内约定俗成的符号。偏离惯例的选择会增加读者的认知负担。

### 原则四：减少符号重载

同一字母不应在不同语境下表示不同的概念，除非语境完全不同且不会混淆。

### 原则五：下标与上标的使用规范

- **下标**：用于索引（$x_i$）、类型标记（$\theta_{\mathrm{init}}$）
- **上标**：用于幂次（$x^2$）、层次（$W^{(l)}$）、迭代（$\theta^{(t)}$）
- 括号区分：层次用 $W^{(l)}$，幂次用 $x^2$（无括号）

---

## 常见符号冲突与解决

### 冲突一：$\sigma$ 的多重含义

- $\sigma$：激活函数（sigmoid）
- $\sigma$：标准差
- $\sigma$：奇异值
- $\sigma$：置换 (permutation)

**解决方法**：
- 激活函数使用具体名称：$\mathrm{sigmoid}(\cdot)$、$\mathrm{ReLU}(\cdot)$
- 标准差：保留 $\sigma$，或在需要区分时使用 $\mathrm{std}$
- 奇异值：使用 $\sigma_i(A)$ 搭配矩阵引数
- 置换：使用 $\pi$ 代替

### 冲突二：$\lambda$ 的多重含义

- $\lambda$：特征值
- $\lambda$：正则化参数
- $\lambda$：速率参数（Poisson 分布）

**解决方法**：
- 特征值：使用 $\lambda_i(A)$ 搭配矩阵引数
- 正则化：使用 $\lambda_{\mathrm{reg}}$ 或直接使用 $\lambda$（根据语境）
- 速率参数：使用 $\mu$ 或希腊字母替代

### 冲突三：$p$ 的多重含义

- $p$：机率 / 机率密度函数
- $p$：范数中的指数（$\ell_p$ 范数）
- $p$：维度或特征数

**解决方法**：
- 机率：保留 $p(\cdot)$ 或 $P(\cdot)$
- 范数指数：保持在下标位置 $\|\cdot\|_p$
- 维度：使用 $d$ 代替

### 冲突四：$H$ 的多重含义

- $H$：熵
- $H$：假设类
- $H$：Hessian 矩阵

**解决方法**：
- 熵：使用 $H(X)$ 带引数
- 假设类：使用 $\mathcal{H}$
- Hessian：使用 $\nabla^2 f$ 或 $\mathbf{H}$（粗体）

### 冲突五：$L$ 的多重含义

- $L$：损失函数
- $L$：Lipschitz 常数
- $L$：网路层数

**解决方法**：
- 损失函数：使用 $\mathcal{L}$ 或 $\ell$
- Lipschitz 常数：保留 $L$
- 网路层数：根据语境使用 $L$ 或 $D$（depth）

---

## 排版建议

### 粗体与花体的区分

| 风格 | 用途 | 范例 |
|------|------|------|
| 粗体小写 $\mathbf{x}$ | 向量 | `\mathbf{x}` |
| 粗体大写 $\mathbf{A}$ | 矩阵 | `\mathbf{A}` |
| 花体 $\mathcal{X}$ | 集合、空间、类 | `\mathcal{X}` |
| 黑板粗体 $\mathbb{R}$ | 数系 | `\mathbb{R}` |
| 正体 $\mathrm{tr}$ | 运算元名称 | `\mathrm{tr}` |

### 自定义命令建议

在论文的 preamble 中定义常用符号，保持一致性并方便修改：

```latex
% 常用集合
\newcommand{\R}{\mathbb{R}}
\newcommand{\N}{\mathbb{N}}
\newcommand{\Z}{\mathbb{Z}}

% 机率与期望
\newcommand{\E}{\mathbb{E}}
\newcommand{\Var}{\mathrm{Var}}
\newcommand{\Cov}{\mathrm{Cov}}
\DeclareMathOperator*{\argmax}{argmax}
\DeclareMathOperator*{\argmin}{argmin}

% 范数与内积
\newcommand{\norm}[1]{\left\lVert #1 \right\rVert}
\newcommand{\abs}[1]{\left\lvert #1 \right\rvert}
\newcommand{\inner}[2]{\left\langle #1, #2 \right\rangle}

% 资讯论
\newcommand{\KL}[2]{D_{\mathrm{KL}}\left(#1 \| #2\right)}
\newcommand{\MI}[2]{I\left(#1; #2\right)}

% 向量与矩阵
\renewcommand{\vec}[1]{\mathbf{#1}}
\newcommand{\mat}[1]{\mathbf{#1}}
```
