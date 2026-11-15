# LaTeX 数学排版模式

本文件涵盖 LaTeX 数学排版的常用模式，包括定理环境设定、排版技巧、对齐方式，
以及矩阵等常用结构。

---

## 必要套件

以下为数学证明排版常需的 LaTeX 套件：

```latex
\usepackage{amsmath}    % 数学环境：align, gather, cases 等
\usepackage{amssymb}    % 数学符号：\mathbb, \because 等
\usepackage{amsthm}     % 定理环境：theorem, proof 等
\usepackage{mathtools}  % amsmath 的增强：\coloneqq, \DeclarePairedDelimiter 等
\usepackage{bm}         % 粗体数学符号 \bm{x}
\usepackage{bbm}        % 黑板粗体数字 \mathbbm{1}（指示函数）
\usepackage{thmtools}   % 定理环境的进阶管理
```

---

## 定理环境设定

### 基本设定 (amsthm)

```latex
% 定理风格：粗体标题、斜体内文
\theoremstyle{plain}
\newtheorem{theorem}{Theorem}[section]
\newtheorem{lemma}[theorem]{Lemma}
\newtheorem{proposition}[theorem]{Proposition}
\newtheorem{corollary}[theorem]{Corollary}
\newtheorem{conjecture}[theorem]{Conjecture}

% 定义风格：粗体标题、正体内文
\theoremstyle{definition}
\newtheorem{definition}[theorem]{Definition}
\newtheorem{example}[theorem]{Example}
\newtheorem{assumption}[theorem]{Assumption}
\newtheorem{condition}[theorem]{Condition}

% 备注风格：斜体标题、正体内文
\theoremstyle{remark}
\newtheorem{remark}[theorem]{Remark}
\newtheorem{note}[theorem]{Note}
\newtheorem{claim}{Claim}
```

**说明**：

- `[section]` 表示编号按章节重设（如 Theorem 3.1）。
- `[theorem]` 表示与 theorem 共用编号计数器，确保顺序编号。
- `claim` 独立编号，不与其他环境共用计数器。

### 未编号版本

```latex
\newtheorem*{theorem*}{Theorem}
\newtheorem*{lemma*}{Lemma}
\newtheorem*{remark*}{Remark}
```

### 自订 QED 符号

```latex
% 预设为空心方块 □
\renewcommand{\qedsymbol}{$\blacksquare$}  % 改为实心方块
```

---

## Theorem / Lemma / Proof 完整范例

### 基本定理与证明

```latex
\begin{theorem}[Pythagorean Theorem]
\label{thm:pythagoras}
  For a right triangle with legs $a$, $b$ and hypotenuse $c$,
  \[
    a^2 + b^2 = c^2.
  \]
\end{theorem}

\begin{proof}
  Consider the square with side length $a + b$. By arranging
  four copies of the triangle inside the square, we obtain ...
  \qed
\end{proof}
```

### 引理与推论

```latex
\begin{lemma}
\label{lem:helper}
  If $f$ is convex and differentiable, then for all $x, y$,
  \[
    f(y) \geq f(x) + \nabla f(x)^\top (y - x).
  \]
\end{lemma}

\begin{proof}
  By convexity, for $t \in (0, 1]$,
  \[
    f(x + t(y - x)) \leq (1 - t)f(x) + tf(y).
  \]
  Rearranging and taking $t \to 0$ yields the result. \qed
\end{proof}

\begin{corollary}
\label{cor:minimum}
  If $\nabla f(x^*) = 0$ and $f$ is convex, then $x^*$ is a
  global minimizer of $f$.
\end{corollary}

\begin{proof}
  By Lemma~\ref{lem:helper}, $f(y) \geq f(x^*) + 0 = f(x^*)$
  for all $y$. \qed
\end{proof}
```

### 带名称的定理

```latex
\begin{theorem}[Jensen's Inequality]
\label{thm:jensen}
  Let $f$ be a convex function and $X$ a random variable with
  $\mathbb{E}[|X|] < \infty$. Then
  \[
    f(\mathbb{E}[X]) \leq \mathbb{E}[f(X)].
  \]
\end{theorem}
```

### 证明草稿 (Proof Sketch)

```latex
\begin{proof}[Proof sketch]
  The main idea is to apply Hoeffding's inequality to each
  hypothesis and then take a union bound over $\mathcal{H}$.
  The full proof is deferred to Appendix~\ref{app:full-proof}.
\end{proof}
```

---

## 等式与公式排版

### 行内公式

```latex
The loss function $\ell(y, \hat{y}) = (y - \hat{y})^2$ is convex.
```

### 展示公式（无编号）

```latex
\[
  f(x) = \sum_{i=1}^n a_i x^i
\]
```

### 展示公式（有编号）

```latex
\begin{equation}
\label{eq:loss}
  \mathcal{L}(\theta) = \frac{1}{n} \sum_{i=1}^n
  \ell(f_\theta(x_i), y_i) + \lambda \|\theta\|_2^2
\end{equation}
```

### 多行对齐 (align)

```latex
\begin{align}
  \mathcal{L}(\theta)
  &= \frac{1}{n} \sum_{i=1}^n \ell(f_\theta(x_i), y_i)
     + \lambda \|\theta\|_2^2 \label{eq:loss-expanded} \\
  &\leq \frac{1}{n} \sum_{i=1}^n \left[
     \ell(f_{\theta^*}(x_i), y_i)
     + \nabla \ell^\top (\theta - \theta^*)
     \right] + \lambda \|\theta\|_2^2 \label{eq:loss-bound} \\
  &= \mathcal{L}(\theta^*) + \text{(remainder terms)}.
     \nonumber
\end{align}
```

**说明**：
- `&` 标记对齐位置（通常放在 `=` 或 `\leq` 前）。
- `\\` 换行。
- `\nonumber` 取消该行的编号。
- 每行可独立加 `\label`。

### 无编号的多行对齐

```latex
\begin{align*}
  (a + b)^2 &= a^2 + 2ab + b^2 \\
  (a - b)^2 &= a^2 - 2ab + b^2
\end{align*}
```

### 多行等式组 (gather)

适用于多个独立的等式，不需要对齐：

```latex
\begin{gather}
  x^2 + y^2 = 1 \label{eq:circle} \\
  z = x + iy \label{eq:complex}
\end{gather}
```

### 子等式 (subequations)

```latex
\begin{subequations}
\label{eq:system}
\begin{align}
  \nabla_x L &= 0 \label{eq:system-x} \\
  \nabla_\lambda L &= 0 \label{eq:system-lambda}
\end{align}
\end{subequations}
```

这会产生 (1a)、(1b) 的编号，而 `\ref{eq:system}` 引用整组。

---

## 分情况讨论

### cases 环境

```latex
\[
  |x| =
  \begin{cases}
    x  & \text{if } x \geq 0, \\
    -x & \text{if } x < 0.
  \end{cases}
\]
```

### dcases 环境 (mathtools)

`dcases` 使用展示模式大小，而 `cases` 使用行内大小：

```latex
\[
  f(x) =
  \begin{dcases}
    \frac{1}{\sqrt{2\pi}} e^{-x^2/2} & \text{if } x > 0, \\
    0 & \text{otherwise}.
  \end{dcases}
\]
```

---

## 矩阵排版

### 基本矩阵

```latex
% 无括号
\[
  \begin{matrix}
    a & b \\
    c & d
  \end{matrix}
\]

% 圆括号
\[
  \begin{pmatrix}
    a & b \\
    c & d
  \end{pmatrix}
\]

% 方括号
\[
  \begin{bmatrix}
    a & b \\
    c & d
  \end{bmatrix}
\]

% 行列式用的双直线
\[
  \begin{vmatrix}
    a & b \\
    c & d
  \end{vmatrix}
\]
```

### 大型矩阵（含省略号）

```latex
\[
  \mathbf{A} =
  \begin{bmatrix}
    a_{11} & a_{12} & \cdots & a_{1n} \\
    a_{21} & a_{22} & \cdots & a_{2n} \\
    \vdots & \vdots & \ddots & \vdots \\
    a_{m1} & a_{m2} & \cdots & a_{mn}
  \end{bmatrix}
\]
```

### 分块矩阵

```latex
\[
  \mathbf{M} =
  \left[
  \begin{array}{c|c}
    \mathbf{A} & \mathbf{B} \\
    \hline
    \mathbf{C} & \mathbf{D}
  \end{array}
  \right]
\]
```

### 行内小矩阵

```latex
The matrix $\bigl(\begin{smallmatrix} a & b \\ c & d
\end{smallmatrix}\bigr)$ is invertible.
```

---

## 括号与定界符

### 自动调整大小

```latex
\left( \frac{a}{b} \right)
\left[ \sum_{i=1}^n x_i \right]
\left\{ x \in \mathbb{R} : x > 0 \right\}
\left\| \mathbf{x} \right\|
\left\langle \mathbf{x}, \mathbf{y} \right\rangle
```

### 手动调整大小

```latex
\big( \Big( \bigg( \Bigg(
\big) \Big) \bigg) \Bigg)
```

**建议**：多数情况使用 `\left...\right`，但在多行公式中（跨行的括号），
需要手动使用 `\big` 系列或 `\left.\right.` 搭配不可见定界符。

### 跨行括号

```latex
\begin{align}
  f(x) &= \biggl( \sum_{i=1}^n a_i x^i \biggr)
           \cdot \biggl( \sum_{j=1}^m b_j x^j \biggr)
\end{align}
```

---

## 常用排版技巧

### 文字在公式中

```latex
\[
  x \in S \quad \text{if and only if} \quad f(x) > 0
\]

\[
  \sum_{i=1}^n x_i \qquad \text{where } x_i \geq 0
\]
```

### 间距控制

| 命令 | 宽度 | 用途 |
|------|------|------|
| `\,` | 薄间距 | 微分符号前 $\int f(x)\,dx$ |
| `\:` | 中间距 | |
| `\;` | 厚间距 | |
| `\quad` | 1em | 公式间分隔 |
| `\qquad` | 2em | 更大的分隔 |
| `\!` | 负薄间距 | 紧缩间距 |

### 数学运算元

```latex
% 预设运算元（正体）
\sin, \cos, \tan, \log, \ln, \exp, \det, \dim, \ker, \lim,
\max, \min, \sup, \inf, \gcd

% 自定义运算元
\DeclareMathOperator{\tr}{tr}
\DeclareMathOperator{\diag}{diag}
\DeclareMathOperator{\sign}{sign}
\DeclareMathOperator{\softmax}{softmax}
\DeclareMathOperator*{\argmax}{argmax}  % * 使下标在展示模式置于正下方
\DeclareMathOperator*{\argmin}{argmin}
```

### 上下标与装饰

```latex
% 上方装饰
\hat{x}        % 估计量
\tilde{x}      % 近似
\bar{x}        % 平均
\overline{AB}  % 长上划线
\widehat{ABC}  % 宽帽子
\widetilde{f}  % 宽波浪

% 向量箭头
\vec{x}        % 小箭头
\overrightarrow{AB}  % 长箭头

% 上下括号
\overbrace{a + b + c}^{\text{sum}}
\underbrace{x_1 + \cdots + x_n}_{n \text{ terms}}
```

### 省略号

```latex
$x_1, x_2, \ldots, x_n$     % 低省略号（逗号列举）
$x_1 + x_2 + \cdots + x_n$  % 中省略号（运算符间）
$\vdots$                      % 垂直省略号
$\ddots$                      % 对角省略号
```

---

## 常见证明结构的排版

### 分步骤证明

```latex
\begin{proof}
  We prove the claim in two steps.

  \textbf{Step 1.}
  We first show that $A$ holds. [Derivation of A.]

  \textbf{Step 2.}
  Using Step~1, we now prove $B$. [Derivation of B using A.]

  Combining Steps~1 and~2, the result follows. \qed
\end{proof}
```

### 归纳法证明

```latex
\begin{proof}
  We proceed by (strong) induction on $n$.

  \textit{Base case} ($n = 1$).
  [Verification for n = 1.]

  \textit{Inductive step}.
  Suppose the claim holds for all $1 \leq j \leq k$.
  We show it for $k + 1$.
  [Derivation using inductive hypothesis.]

  By induction, the result holds for all $n \geq 1$. \qed
\end{proof}
```

### 反证法证明

```latex
\begin{proof}
  Suppose, for the sake of contradiction, that [negation].
  [Derivation leading to contradiction.]
  This contradicts [known fact], completing the proof. \qed
\end{proof}
```

### 充要条件证明

```latex
\begin{proof}
  ($\Rightarrow$)
  Assume $A$ holds. [Derivation showing $B$.]

  ($\Leftarrow$)
  Assume $B$ holds. [Derivation showing $A$.] \qed
\end{proof}
```

---

## 交叉引用

### 基本引用

```latex
By Theorem~\ref{thm:main}, ...
As shown in Equation~\eqref{eq:bound}, ...
See Lemma~\ref{lem:aux} and Corollary~\ref{cor:result}.
```

**注意**：
- 定理等环境用 `\ref`。
- 等式用 `\eqref`（自动加括号）。
- `~` 为不可断行空格，防止引用编号与前文断行。

### cleveref 套件（推荐）

```latex
\usepackage{cleveref}

% 自动判断引用类型
\cref{thm:main}         % → Theorem 1
\Cref{thm:main}         % → Theorem 1 (句首大写)
\cref{eq:bound}          % → (1)
\cref{lem:a,lem:b,lem:c} % → Lemmas 1, 2 and 3
```

---

## 附录中的定理环境

论文附录中的定理通常需要不同的编号格式：

```latex
\appendix

% 方法一：重设计数器
\setcounter{theorem}{0}
\renewcommand{\thetheorem}{\Alph{section}.\arabic{theorem}}

% 方法二：使用 restatable 环境 (thmtools)
% 在正文中：
\begin{restatable}{theorem}{maintheorem}
\label{thm:main}
  Statement of the main theorem.
\end{restatable}

% 在附录中重新陈述：
\maintheorem*
\begin{proof}
  Full proof here. \qed
\end{proof}
```

---

## 常见排版问题与解决

### 问题一：括号大小不匹配

```latex
% 错误：\left \right 跨行
\begin{align}
  f(x) &= \left( \sum_{i=1}^n x_i \right. \\  % 报错！
       &\quad \left. + y \right)
\end{align}

% 正确：使用 \bigl \bigr 或不可见定界符
\begin{align}
  f(x) &= \biggl( \sum_{i=1}^n x_i \nonumber \\
       &\quad + y \biggr)
\end{align}
```

### 问题二：长公式断行

```latex
% 使用 multline 环境
\begin{multline}
  \mathcal{L}(\theta) = \frac{1}{n} \sum_{i=1}^n
  \ell(f_\theta(x_i), y_i) \\
  + \lambda_1 \|\theta\|_1 + \lambda_2 \|\theta\|_2^2
  + \gamma \sum_{j} R_j(\theta)
\end{multline}

% 或使用 split 在 equation 内
\begin{equation}
\begin{split}
  \mathcal{L}(\theta) &= \frac{1}{n} \sum_{i=1}^n
  \ell(f_\theta(x_i), y_i) \\
  &\quad + \lambda_1 \|\theta\|_1
  + \lambda_2 \|\theta\|_2^2
\end{split}
\end{equation}
```

### 问题三：条件机率中的 | 大小

```latex
% 错误：| 太短
p(y | x)

% 正确方案
p(y \mid x)                          % \mid 有适当间距
p\left(y \,\middle|\, x\right)      % 自动调整大小
p(y \given x)                        % 自定义命令（见下）

% 自定义命令
\newcommand{\given}{\,\middle|\,}
```

### 问题四：积分的排版

```latex
% 推荐风格：微分符号前加薄间距
\int_0^\infty f(x) \, dx

% 多重积分
\iint_D f(x, y) \, dx \, dy
\iiint_V f(x, y, z) \, dx \, dy \, dz

% 正体 d（某些风格指南要求）
\newcommand{\dd}{\mathrm{d}}
\int_0^\infty f(x) \, \dd x
```

### 问题五：最佳化问题的排版

```latex
\[
  \min_{\theta \in \Theta} \quad
  \frac{1}{n} \sum_{i=1}^n \ell(f_\theta(x_i), y_i)
  \quad \text{s.t.} \quad \|\theta\| \leq B
\]

% 更正式的排版
\[
  \begin{aligned}
    \minimize_{\theta} \quad
    & \frac{1}{n} \sum_{i=1}^n \ell(f_\theta(x_i), y_i) \\
    \text{subject to} \quad
    & \|\theta\|_2 \leq B, \\
    & \theta_j \geq 0, \quad j = 1, \ldots, d.
  \end{aligned}
\]

% 所需的自定义命令
\DeclareMathOperator{\minimize}{minimize}
\DeclareMathOperator{\maximize}{maximize}
```

---

## 完整证明排版范例

以下是一个完整的定理及其证明的排版范例：

```latex
\begin{theorem}[Generalization Bound for Finite Hypothesis Classes]
\label{thm:finite-gen-bound}
  Let $\mathcal{H}$ be a finite hypothesis class and let
  $S = \{(x_i, y_i)\}_{i=1}^n$ be drawn i.i.d.\ from a
  distribution $\mathcal{D}$. Assume the loss function $\ell$
  is bounded in $[0, 1]$. Then, for any $\delta > 0$, with
  probability at least $1 - \delta$ over the draw of $S$,
  for all $h \in \mathcal{H}$:
  \begin{equation}
  \label{eq:gen-bound}
    \left| R(h) - \hat{R}_n(h) \right|
    \leq \sqrt{\frac{\ln|\mathcal{H}| + \ln(2/\delta)}{2n}},
  \end{equation}
  where $R(h) = \mathbb{E}_{(x,y) \sim \mathcal{D}}[\ell(h(x), y)]$
  and $\hat{R}_n(h) = \frac{1}{n}\sum_{i=1}^n \ell(h(x_i), y_i)$.
\end{theorem}

\begin{proof}
  Fix any $h \in \mathcal{H}$. Define $Z_i = \ell(h(x_i), y_i)$
  for $i = 1, \ldots, n$. Since $\ell$ is bounded in $[0, 1]$,
  the $Z_i$ are i.i.d.\ random variables in $[0, 1]$ with mean
  $\mu = R(h)$.

  \textbf{Step 1} (Concentration for a single hypothesis).
  By Hoeffding's inequality,
  \begin{equation}
  \label{eq:hoeffding-single}
    \Pr\!\left[\left|\hat{R}_n(h) - R(h)\right| > \epsilon\right]
    \leq 2\exp(-2n\epsilon^2).
  \end{equation}

  \textbf{Step 2} (Union bound over $\mathcal{H}$).
  Applying the union bound over all $h \in \mathcal{H}$:
  \begin{align}
    \Pr\!\left[\exists\, h \in \mathcal{H}:
      \left|\hat{R}_n(h) - R(h)\right| > \epsilon\right]
    &\leq \sum_{h \in \mathcal{H}}
      \Pr\!\left[\left|\hat{R}_n(h) - R(h)\right|
      > \epsilon\right] \nonumber \\
    &\leq |\mathcal{H}| \cdot 2\exp(-2n\epsilon^2).
      \label{eq:union-bound}
  \end{align}

  \textbf{Step 3} (Solving for $\epsilon$).
  Setting the right-hand side of~\eqref{eq:union-bound} equal
  to $\delta$ and solving for $\epsilon$:
  \[
    2|\mathcal{H}|\exp(-2n\epsilon^2) = \delta
    \quad \Longrightarrow \quad
    \epsilon = \sqrt{\frac{\ln|\mathcal{H}| + \ln(2/\delta)}{2n}}.
  \]

  Substituting back, with probability at least $1 - \delta$,
  for all $h \in \mathcal{H}$,
  $|R(h) - \hat{R}_n(h)| \leq \epsilon$. This
  establishes~\eqref{eq:gen-bound}. \qed
\end{proof}
```
