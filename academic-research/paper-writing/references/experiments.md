# Experiments 实验撰写指南

## 核心原则

Experiments section 的目标是**用数据说服 reviewer 你的方法有效**。每一个 Introduction 中的 claim 都必须在这里找到对应的实验支持。遵循四段式结构：Setup → Main Results → Ablation Study → Analysis。

---

## 四段式结构

### 第 1 段：Experimental Setup

#### 必须包含的资讯

```latex
\subsection{Experimental Setup}
\label{sec:setup}

\paragraph{Datasets.}
% 列出所有使用的资料集，每个都要说明：
% - 资料集名称与引用
% - 规模（图片数、场景数等）
% - 训练/验证/测试分割方式
% - 为什么选这个资料集
We evaluate on three standard benchmarks:
(1)~\textbf{DTU}~\cite{dtu} (124 scenes, ...),
(2)~\textbf{BlendedMVS}~\cite{blendedmvs} (113 scenes, ...),
and (3)~\textbf{Tanks\&Temples}~\cite{tnt} (21 scenes, ...).
We follow the standard training/test split of [ref].

\paragraph{Baselines.}
% 列出所有比较的 baseline
% - 每个 baseline 的引用
% - 简述方法类型
% - 结果来源（原论文 or 自己跑的）
We compare against X recent methods spanning two families:
regression-based approaches (PixelNeRF~\cite{pixelnerf},
MVSNeRF~\cite{mvsnerf}, ...) and generative approaches
(SparseFusion~\cite{sparsefusion}, ...).
All baseline results are reproduced using official code
with default hyperparameters, except [X] where we report
numbers from the original paper.

\paragraph{Metrics.}
% 列出所有使用的指标
% - 指标的全名与缩写
% - 每个指标衡量什么
We report PSNR, SSIM~\cite{ssim}, and
LPIPS~\cite{lpips} for image quality evaluation.
Higher is better for PSNR and SSIM; lower is better
for LPIPS.

\paragraph{Implementation Details.}
% 可重现性的关键
% - 框架（PyTorch版本）
% - 优化器、学习率、排程
% - 训练 epoch 数
% - batch size
% - 硬体环境
% - 训练时间
Our method is implemented in PyTorch 2.0. We train for
100K iterations using Adam~\cite{adam} with a learning
rate of $5 \times 10^{-4}$, decayed by 0.5 every 25K
iterations. Training takes approximately 8 hours on a
single NVIDIA A100 GPU. Detailed hyperparameters are
provided in the supplementary material.
```

#### 常见遗漏

| 遗漏项目 | Reviewer 反应 |
|---------|-------------|
| 资料集分割方式 | "How was the data split?" |
| Baseline 结果来源 | "Were baselines re-run or taken from papers?" |
| 训练超参数 | "Cannot reproduce" |
| 硬体资讯 | "What is the computational cost?" |
| 随机种子 | "How many runs? What is the variance?" |

### 第 2 段：Main Results

#### 表格设计原则

主结果表格是 Experiments 的核心。设计原则如下：

**格式规范**：
- 使用 `booktabs` 套件（`\toprule`, `\midrule`, `\bottomrule`）
- **最佳结果加粗**（`\textbf{}`）
- **次佳结果加底线**（`\underline{}`）
- 在 caption 中说明加粗和底线的含义
- 方法名称按年份排列或按类别分组
- 你的方法放在表格最后一行
- 用 `\midrule` 将你的方法与 baseline 分隔

```latex
\begin{table}[t]
  \centering
  \caption{Quantitative comparison on DTU~\cite{dtu} with
    3 input views. \textbf{Bold}: best result.
    \underline{Underline}: second best.
    $\dagger$: results from original papers.}
  \label{tab:main_dtu}
  \begin{tabular}{lccc}
    \toprule
    Method & PSNR$\uparrow$ & SSIM$\uparrow$ & LPIPS$\downarrow$ \\
    \midrule
    PixelNeRF~\cite{pixelnerf} & 19.31 & 0.789 & 0.382 \\
    MVSNeRF~\cite{mvsnerf} & 21.18 & 0.843 & 0.264 \\
    SparseNeRF~\cite{sparsenerf}$^\dagger$ & 22.45 & 0.871 & 0.218 \\
    RegNeRF~\cite{regnerf} & \underline{23.12} & \underline{0.889} & \underline{0.195} \\
    \midrule
    Ours & \textbf{25.41} & \textbf{0.912} & \textbf{0.163} \\
    \bottomrule
  \end{tabular}
\end{table}
```

**箭头标注**：在指标名称旁加上 $\uparrow$（越高越好）或 $\downarrow$（越低越好），帮助读者快速判读。

#### 文字描述

表格本身只呈现数字，文字需要帮助读者**解读**这些数字：

```latex
% ✅ 好的结果描述
\cref{tab:main_dtu} presents the quantitative comparison
on DTU. Our method achieves 25.41 dB PSNR, outperforming
the previous best (RegNeRF, 23.12 dB) by 2.29 dB.
Notably, this improvement is most pronounced in scenes
with large occluded regions (see per-scene breakdown
in supplementary), confirming the effectiveness of our
geometric guidance.

% ❌ 坏的结果描述（只重复表格数字）
As shown in Table 1, our PSNR is 25.41, SSIM is 0.912,
and LPIPS is 0.163. PixelNeRF achieves 19.31, MVSNeRF
achieves 21.18, SparseNeRF achieves 22.45, RegNeRF
achieves 23.12.
```

**要点**：
- 不要逐行重复表格数字
- 聚焦于**趋势**和**洞察**
- 解释为什么你的方法更好（与 Method 的 claim 对应）
- 指出在哪些情境下优势最明显

#### 多资料集呈现

如果在多个资料集上实验：
- 每个资料集一张表格，或合并成一张大表
- 文字描述聚焦于跨资料集的一致趋势
- 如果某个资料集表现不如预期，诚实说明原因

### 第 3 段：Ablation Study

Ablation study 是 reviewer 最看重的实验之一。它证明你的方法中**每个组件都是必要的**。

#### 设计原则

```
完整方法（Full model）
  - 去掉组件 A → 验证 A 的必要性
  - 去掉组件 B → 验证 B 的必要性
  - 去掉组件 C → 验证 C 的必要性
  - 替换组件 A 为替代方案 A' → 验证 A 的设计选择
  - 改变超参数 → 验证超参数敏感度
```

#### 表格范例

```latex
\begin{table}[t]
  \centering
  \caption{Ablation study on DTU with 3 input views.
    Each row removes or replaces one component from
    the full model.}
  \label{tab:ablation}
  \begin{tabular}{lccc}
    \toprule
    Configuration & PSNR & SSIM & LPIPS \\
    \midrule
    Full model & \textbf{25.41} & \textbf{0.912} & \textbf{0.163} \\
    \midrule
    w/o geometry proxy & 23.05 & 0.878 & 0.214 \\
    w/o feature conditioning & 24.18 & 0.895 & 0.188 \\
    w/o depth supervision & 24.72 & 0.903 & 0.175 \\
    Replace cost volume $\to$ monocular depth & 24.33 & 0.891 & 0.192 \\
    \bottomrule
  \end{tabular}
\end{table}
```

#### 文字描述

```latex
\cref{tab:ablation} presents the ablation study. Removing
the geometry proxy causes the largest performance drop
($-$2.36 dB), confirming that explicit geometric guidance
is the key ingredient of our framework. Feature conditioning
contributes 1.23 dB, demonstrating the importance of
geometry-aware features. Replacing our cost-volume-based
geometry estimation with monocular depth reduces PSNR by
1.08 dB, validating our choice of leveraging multi-view
geometry.
```

### 第 4 段：Analysis

超越数字的深入分析，展示你对方法的理解：

#### 常见分析类型

| 分析类型 | 内容 | 呈现方式 |
|---------|------|---------|
| 定性比较 | 视觉结果对比 | Figure（并排对比图） |
| 失败案例 | 方法失效的场景 | Figure + 分析文字 |
| 效率分析 | 推理时间、参数量、FLOPs | Table |
| Scaling 分析 | 随视角数/资料量/模型大小的变化 | Line chart |
| 泛化性分析 | 在新资料集/新场景上的表现 | Table / Figure |
| 超参数敏感度 | 关键超参数的影响 | Line chart / Table |

#### 定性比较范例

```latex
\paragraph{Qualitative Comparison.}
\cref{fig:qualitative} presents visual comparisons on
challenging scenes from DTU. Our method produces sharper
textures and more coherent geometry in occluded regions
(highlighted in red boxes), whereas PixelNeRF generates
blurry results and RegNeRF exhibits floating artifacts.
```

#### 失败案例分析

```latex
\paragraph{Failure Cases.}
\cref{fig:failure} shows representative failure cases.
Our method struggles with (1)~highly specular surfaces
where the Lambertian assumption of our cost volume
breaks down, and (2)~extremely thin structures that
fall between depth sampling planes. Addressing these
limitations is an important direction for future work.
```

---

## 超参数描述

### 在正文中

只提及最关键的超参数（影响方法设计的）：

```latex
We set the number of depth hypotheses to $D = 128$,
uniformly sampled in inverse depth space between the
near and far planes. The loss weights are set to
$\lambda_d = 0.1$ and $\lambda_r = 0.01$ based on
validation performance.
```

### 在附录/补充材料中

提供完整的超参数表格：

```latex
\begin{table}[h]
  \centering
  \caption{Complete hyperparameter settings.}
  \begin{tabular}{lc}
    \toprule
    Hyperparameter & Value \\
    \midrule
    Learning rate & $5 \times 10^{-4}$ \\
    Batch size & 4 \\
    Optimizer & Adam ($\beta_1 = 0.9$, $\beta_2 = 0.999$) \\
    LR schedule & Step decay ($\times 0.5$ every 25K) \\
    Total iterations & 100K \\
    Depth hypotheses $D$ & 128 \\
    $\lambda_d$ & 0.1 \\
    $\lambda_r$ & 0.01 \\
    \bottomrule
  \end{tabular}
\end{table}
```

---

## 公平比较原则

Reviewer 非常在意比较的公平性：

1. **相同资料分割**：所有方法使用完全相同的训练/测试集
2. **相同输入**：相同的输入图片、相同的视角
3. **相同评估方式**：相同的指标计算方式（resolution、cropping 等）
4. **最佳设定**：baseline 使用其论文中推荐的最佳设定
5. **版本说明**：如果使用官方程式码，说明版本；如果自己实现，说明依据

```latex
% 公平性声明
For fair comparison, all methods are evaluated at
$800 \times 600$ resolution. We use the official
implementations of all baselines with their recommended
hyperparameters. For methods that do not provide pretrained
models on our evaluation datasets, we retrain them
following the original training protocols.
```

---

## 统计显著性

对于结果差异较小的比较，建议报告统计显著性：

```latex
We run each experiment 3 times with different random
seeds and report the mean and standard deviation.
Our method achieves $25.41 \pm 0.12$ dB PSNR,
compared to $23.12 \pm 0.08$ dB for RegNeRF.
The improvement is statistically significant
($p < 0.01$, paired $t$-test).
```

---

## 自我检查清单

```
□ Experimental Setup 是否包含资料集、baseline、指标、实现细节？
□ 是否所有 Introduction 中的 claim 都有对应实验？
□ 主结果表格是否加粗最佳、底线次佳？
□ 文字是否解读趋势（而非重复数字）？
□ Ablation study 是否验证每个组件的必要性？
□ 是否有定性比较（视觉结果）？
□ 是否有失败案例分析？
□ 是否有效率比较？
□ 比较是否公平（相同设定）？
□ 超参数是否有完整记录？
□ 是否报告多次实验的方差？
```

---

*回到主文件 → `../SKILL.md`*
