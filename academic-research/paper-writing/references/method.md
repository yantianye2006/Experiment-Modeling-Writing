# Method 方法撰写指南

## 核心原则

Method section 是论文的技术核心。它必须让读者（1）理解你的方法的高层逻辑，（2）掌握每个组件的技术细节，（3）明白每个设计选择背后的理由。遵循三要素结构：Overview → Details → Justification。

---

## 三要素结构

### 要素 1：Overview（方法概览）

Method 的第一段（或第一个 subsection）必须提供方法的高层概览，让读者在深入细节前先掌握全貌。

**必须包含**：
- 方法的整体流程
- 输入和输出是什么
- 主要组件有哪些
- 各组件之间的关系

**范例**：
```latex
\section{Method}
\label{sec:method}

Given a set of $K$ input images $\{I_k\}_{k=1}^{K}$ with
known camera poses $\{P_k\}_{k=1}^{K}$, our goal is to
reconstruct a neural scene representation that enables
high-quality novel view synthesis.

\cref{fig:overview} illustrates our framework, which consists
of three stages: (1)~a \textit{geometry estimation} module
that constructs a coarse depth proxy from the input views
(Sec.~\ref{sec:geometry}), (2)~a \textit{feature extraction}
module that computes geometry-aware local features
(Sec.~\ref{sec:features}), and (3)~a \textit{neural rendering}
module that synthesizes novel views conditioned on the
estimated geometry and features (Sec.~\ref{sec:rendering}).
```

**注意事项**：
- 必须引用 overview figure（通常是 Figure 2 或 Figure 1）
- 用括号标注每个组件对应的 subsection
- 使用 `\cref{}` 或 `Sec.~\ref{}` 做交叉引用

### 要素 2：Details（技术细节）

每个组件用一个 subsection 详细描述。每个 subsection 遵循以下结构：

```
1. 动机（为什么需要这个组件？）     ← Motivation-First
2. 形式化定义（输入、输出、操作）    ← 数学严谨
3. 具体实现（网路架构、损失函数等）   ← 可重现
4. 与其他选择的比较（为什么选这个？） ← Justification
```

**范例**：
```latex
\subsection{Geometry Estimation}
\label{sec:geometry}

% 1. 动机
Directly optimizing a neural radiance field from sparse
views is ill-posed, as large portions of the scene lack
multi-view supervision. To provide geometric guidance for
unobserved regions, we first estimate a coarse depth map
for each input view.

% 2. 形式化定义
Specifically, for each pair of input views $(I_i, I_j)$,
we construct a cost volume $\mathbf{C}_{ij} \in
\mathbb{R}^{H \times W \times D}$ by computing feature
correlations at $D$ depth hypotheses uniformly sampled
in inverse depth space:
\begin{equation}
  \mathbf{C}_{ij}(u, v, d) = \langle
    \mathbf{F}_i(u, v),\;
    \mathbf{F}_j(\pi(P_j P_i^{-1}, u, v, d))
  \rangle,
  \label{eq:cost_volume}
\end{equation}
where $\mathbf{F}_i$ denotes the feature map of view $i$,
$\pi(\cdot)$ is the projection function, and $\langle
\cdot, \cdot \rangle$ is the inner product.

% 3. 具体实现
The cost volume is regularized by a 3D U-Net with group
normalization, producing a probability volume from which
we extract the depth via soft argmin~\cite{gcnet}.
We aggregate depth estimates from all view pairs using
a confidence-weighted average.

% 4. 与其他选择的比较
We opt for a cost-volume-based approach over monocular
depth estimation~\cite{midas} because it explicitly
leverages multi-view geometry, providing more reliable
estimates in overlapping regions
(see ablation in \cref{tab:ablation}).
```

### 要素 3：Justification（合理性论证）

每一个非平凡的设计选择都需要 justification。有三种 justification 方式：

| 方式 | 适用场景 | 范例 |
|------|---------|------|
| 理论 | 有数学推导支持 | "By Theorem 1, this loss is equivalent to..." |
| 实证 | 有 ablation 支持 | "As shown in Table 3, this design improves by 1.2 dB" |
| 直觉 | 合理的设计直觉 | "Since depth discontinuities often align with semantic boundaries, we..." |

**最强的 justification** 结合理论与实证：先用直觉解释为什么这样设计，再用 ablation 验证。

---

## 如何用图说明 Pipeline

### Overview Figure 设计原则

Overview figure（通常是 Figure 2）是 Method section 最重要的图：

1. **从左到右或从上到下的资讯流**：输入在左/上，输出在右/下
2. **模组化呈现**：每个组件用一个方框表示，方框内用简短标签
3. **标注对应的 subsection**：让读者知道去哪里看细节
4. **使用一致的颜色系统**：
   - 输入/输出用一种颜色
   - 可训练模组用另一种颜色
   - 损失函数用第三种颜色
5. **避免过度复杂**：如果超过 7 个方框，考虑分层呈现

### Caption 写作

```latex
\caption{Overview of our proposed framework. Given $K$
  sparse input views (left), we first estimate coarse
  geometry through a cost volume (Sec.~\ref{sec:geometry}),
  then extract geometry-aware features
  (Sec.~\ref{sec:features}), and finally render novel
  views through a conditioned neural radiance field
  (Sec.~\ref{sec:rendering}). Trainable components are
  shown in \textcolor{blue}{blue}; frozen modules in gray.}
```

### 补充图

除了 overview figure，Method section 可能需要：
- **细节图**：展示某个关键组件的内部结构
- **示意图**：用视觉方式解释某个抽象概念
- **比较图**：展示你的方法与 baseline 的结构差异

---

## 符号一致性要求

### 首次出现规则

每个数学符号在首次出现时必须定义：

```latex
% ✅ 首次出现时定义
Given a set of $K$ input images $\{I_k\}_{k=1}^{K}$...

% ❌ 使用未定义的符号
We compute $\mathbf{C}_{ij}(u,v,d)$...
% （读者不知道 C, u, v, d 分别是什么）
```

### 符号表（Notation Table）

对于符号众多的论文，建议在 Method 开头或附录中放一个符号表：

```latex
\begin{table}[t]
  \centering
  \caption{Notation summary.}
  \label{tab:notation}
  \begin{tabular}{cl}
    \toprule
    Symbol & Description \\
    \midrule
    $K$ & Number of input views \\
    $I_k$ & The $k$-th input image \\
    $P_k$ & Camera pose of the $k$-th view \\
    $\mathbf{F}_k$ & Feature map of the $k$-th view \\
    $\mathbf{C}_{ij}$ & Cost volume between views $i$ and $j$ \\
    $\hat{D}_k$ & Estimated depth map for view $k$ \\
    \bottomrule
  \end{tabular}
\end{table}
```

### 常见符号不一致问题

| 问题 | 范例 | 修正 |
|------|------|------|
| 同一概念用不同符号 | 有时用 $x$，有时用 $\mathbf{x}$ | 统一为一种 |
| 不同概念用相同符号 | 损失函数和长度都用 $L$ | 损失用 $\mathcal{L}$，长度用 $L$ |
| 上下标不一致 | 有时 $x_i$，有时 $x^{(i)}$ | 统一风格 |
| 缺少定义 | 突然出现 $\lambda$ | 加上 "where $\lambda$ is the balancing weight" |

---

## 损失函数撰写

损失函数是 Method 的重要部分，需要特别注意写法：

### 结构

```latex
\subsection{Training Objective}
\label{sec:loss}

% 1. 总损失
Our total training objective combines three terms:
\begin{equation}
  \mathcal{L} = \mathcal{L}_{\text{rgb}}
    + \lambda_d \mathcal{L}_{\text{depth}}
    + \lambda_r \mathcal{L}_{\text{reg}},
  \label{eq:total_loss}
\end{equation}
where $\lambda_d$ and $\lambda_r$ are balancing weights.

% 2. 逐项定义
\paragraph{Reconstruction Loss.}
$\mathcal{L}_{\text{rgb}}$ measures the photometric
error between rendered and ground-truth pixels:
\begin{equation}
  \mathcal{L}_{\text{rgb}} = \frac{1}{|\mathcal{R}|}
    \sum_{\mathbf{r} \in \mathcal{R}}
    \| \hat{C}(\mathbf{r}) - C(\mathbf{r}) \|_2^2,
  \label{eq:rgb_loss}
\end{equation}
where $\mathcal{R}$ is the set of sampled rays...

% 3. 解释为什么用这个损失
We use L2 rather than L1 loss as it provides smoother
gradients during early training when the geometry
estimate is coarse.
```

### 注意事项

- 每个损失项都要单独定义
- 每个超参数（$\lambda$）都要说明如何设定
- 解释为什么选择这个损失函数（而非其他选择）

---

## 演算法虚拟码

对于流程复杂的方法，演算法虚拟码可以帮助读者理解：

**何时需要**：
- 方法有明确的多步骤流程
- 文字描述容易混淆
- 训练和推理流程不同

**何时不需要**：
- 方法流程很直觉（一个 forward pass）
- Overview figure 已经足够清晰

---

## 常见错误

### 错误 1：缺少 Overview

直接跳入技术细节，读者迷失在符号和公式中。

**解法**：Method 第一段必须是不带公式的高层概览。

### 错误 2：缺少 Motivation

```latex
% ❌ 没有动机
We add a skip connection between layers 3 and 7.

% ✅ 有动机
To preserve fine-grained spatial details that are
often lost through successive downsampling, we
introduce a skip connection between layers 3 and 7.
```

### 错误 3：细节不足以重现

```latex
% ❌ 太含糊
We use a CNN to extract features.

% ✅ 可重现
We use a ResNet-50~\cite{resnet} pretrained on ImageNet
as the feature extractor. We extract features from the
output of \texttt{layer3}, yielding feature maps of
dimension $\mathbb{R}^{H/8 \times W/8 \times 1024}$.
```

### 错误 4：符号混乱

同一个符号在不同地方表示不同的东西，或者同一概念用了不同符号。

**解法**：全文写完后，做一次符号一致性检查。

---

## 自我检查清单

```
□ 是否有清晰的 Overview（不带公式）？
□ Overview 是否引用了 figure？
□ 每个组件是否有独立的 subsection？
□ 每个设计选择是否有 motivation？
□ 所有符号是否在首次出现时定义？
□ 符号是否全文一致？
□ 损失函数是否逐项定义？
□ 超参数是否说明设定方式？
□ 细节是否足够让人重现？
□ 是否需要演算法虚拟码？
```

---

*回到主文件 → `../SKILL.md`*
