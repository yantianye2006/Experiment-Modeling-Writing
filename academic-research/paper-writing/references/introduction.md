# Introduction 引言写作指南

## 核心原则

Introduction 是论文中最难写的部分。它决定了 reviewer 是否认为你的工作值得被接收。一个好的 Introduction 必须在 1-1.5 页内完成一个完整的逻辑论证：这个问题重要→现有方法不够好→我们有更好的解法→我们的贡献如下。

---

## 漏斗结构（Funnel Structure）

Introduction 的逻辑必须遵循由宽到窄的漏斗结构：

```
┌─────────────────────────────────────────┐
│         大背景（宽）                       │
│    这个研究领域为什么重要？                   │
├─────────────────────────────────────────┤
│       具体问题（中）                        │
│    在这个领域中，什么问题尚未解决？             │
├─────────────────────────────────────────┤
│     现有方法的不足（窄）                     │
│    现有方法为什么不够好？                     │
├─────────────────────────────────────────┤
│      我们的方法（核心）                      │
│    我们怎么解决这个问题？                     │
├─────────────────────────────────────────┤
│       贡献列表                            │
│    具体列出 3-4 个贡献                      │
└─────────────────────────────────────────┘
```

### 第 1 段：大背景

- **目标**：建立共识——这个研究领域为什么重要
- **长度**：3-5 句
- **技巧**：
  - 从应用或现实需求切入
  - 不要太宽泛（"Deep learning has achieved great success..."）
  - 也不要太窄（直接跳到你的具体问题）
  - 引用 2-3 篇高影响力的论文建立可信度

**范例**：
```latex
Understanding and generating 3D scenes from images is a
cornerstone of computer vision, with direct applications
in autonomous driving~\cite{ref1}, robotic
manipulation~\cite{ref2}, and augmented
reality~\cite{ref3}. Recent advances in neural scene
representations~\cite{nerf,instant_ngp} have demonstrated
remarkable quality in novel view synthesis, sparking
widespread interest in learning-based 3D reconstruction.
```

### 第 2 段：具体问题

- **目标**：从大背景聚焦到你要解决的具体问题
- **长度**：3-5 句
- **技巧**：
  - 明确定义问题的边界
  - 说明这个问题为什么特别困难
  - 用一句话概括问题的核心挑战

**范例**：
```latex
Despite this progress, most existing methods require dense
multi-view inputs (typically 50--100 images) to achieve
high-quality reconstruction. In many practical scenarios,
however, only a sparse set of views (e.g., 3--5 images)
is available. Reconstructing from such sparse inputs is
fundamentally ill-posed, as large portions of the scene
remain unobserved.
```

### 第 3 段：现有方法的不足

- **目标**：指出现有方法的具体缺陷，为你的方法建立必要性
- **长度**：4-6 句
- **技巧**：
  - 分类介绍现有方法的主要流派
  - 每个流派指出一个核心缺陷
  - 缺陷必须是客观的、可验证的
  - **不要攻击先前工作**，而是客观分析其限制

**范例**：
```latex
Prior approaches to sparse-view reconstruction fall into
two categories. Regression-based methods~\cite{pixelnerf,mvsnerf}
directly predict radiance fields from input views but
struggle with unseen regions, producing blurry artifacts.
Generative approaches~\cite{sparsefusion,zero123} leverage
diffusion priors to hallucinate novel views, yet often
generate geometrically inconsistent content. Both families
lack an explicit mechanism to reason about scene geometry
at a global level, limiting their ability to produce
coherent reconstructions.
```

### 第 4 段：我们的方法

- **目标**：介绍你的核心 idea 和方法概览
- **长度**：4-6 句
- **技巧**：
  - **Motivation-First**：先说为什么这样做，再说怎么做
  - 用一句话概括核心 insight
  - 然后简要描述方法的主要组件
  - 避免技术细节（留给 Method section）
  - 可以在这里预览关键结果

**范例**：
```latex
Our key observation is that even a coarse geometric
estimate---such as a rough depth map or voxel grid---provides
sufficient structural guidance to regularize the
reconstruction in unobserved regions. Building on this
insight, we present SparseRecon, a coarse-to-fine framework
that first constructs an approximate geometry proxy from
the available views using a lightweight stereo network,
then progressively refines the scene representation through
a geometry-conditioned neural implicit model. This design
decouples the problem into tractable sub-tasks: global
structure estimation and local detail refinement.
```

### 第 5 段：贡献列表

- **目标**：以清单形式明确列出 3-4 个贡献
- **格式**：使用 `\begin{itemize}` 或 `\begin{enumerate}`
- **技巧**：
  - 每个贡献必须是**具体的、可验证的**
  - 第一个贡献通常是方法本身
  - 第二个贡献通常是某个技术创新点
  - 最后一个贡献通常是实验结果
  - 避免说 "We are the first to..."（除非你 100% 确定）

**范例**：
```latex
In summary, our contributions are as follows:
\begin{itemize}
  \item We propose SparseRecon, a coarse-to-fine framework
    for sparse-view 3D reconstruction that explicitly
    leverages geometric priors to guide neural scene
    representations.
  \item We introduce a geometry-conditioned refinement
    module that adaptively allocates representational
    capacity based on the local geometric complexity,
    enabling detailed reconstruction in complex regions
    while maintaining efficiency.
  \item Extensive experiments on three benchmarks (DTU,
    BlendedMVS, Tanks\&Temples) demonstrate that SparseRecon
    outperforms existing methods by 2.3~dB PSNR on average
    using only 3 input views, while running 5$\times$ faster
    than the nearest competitor.
\end{itemize}
```

---

## 贡献列表写作要诀

### 好的贡献 vs 坏的贡献

```latex
% ❌ 太含糊、不可验证
\item We propose a novel method for 3D reconstruction.

% ❌ 过度宣称
\item We are the first to solve sparse-view reconstruction.

% ❌ 只是实作细节
\item We implement our method in PyTorch.

% ✅ 具体、可验证
\item We propose a coarse-to-fine framework that decouples
  sparse-view reconstruction into geometry estimation and
  appearance refinement, reducing the problem complexity.

% ✅ 有数字支撑
\item Extensive experiments demonstrate state-of-the-art
  performance on three benchmarks, with 2.3 dB improvement
  in PSNR using 3$\times$ fewer input views.
```

### 贡献的数量

- **最佳**：3 个贡献
- **可接受**：2-4 个贡献
- **过多**：5 个以上（会让 reviewer 觉得你在灌水）
- **过少**：1 个（会让 reviewer 觉得贡献不够）

### 贡献的类型组合

推荐的组合方式：

| 贡献 1 | 贡献 2 | 贡献 3 |
|--------|--------|--------|
| 方法/框架 | 技术创新 | 实验结果 |
| 问题定义 | 解法 | 理论分析 + 实验 |
| 新观点/insight | 基于 insight 的方法 | 大规模实验验证 |

---

## 常见错误

### 错误 1：背景太长

```latex
% ❌ 整整一段都在讲 deep learning 的历史
Deep learning has achieved remarkable progress in the past
decade. Starting from AlexNet in 2012, convolutional neural
networks have dominated...

% ✅ 直接切入相关背景
3D scene understanding from images is fundamental to
robotics and AR applications.
```

### 错误 2：漏斗结构断裂

问题描述和方法之间没有逻辑衔接——reader 不知道为什么你的方法能解决前面提到的问题。

**解法**：在描述方法前，用一句 "key observation" 或 "key insight" 连接问题和解法。

### 错误 3：贡献列表与正文不符

Introduction 宣称的贡献在后文找不到对应的章节或实验。

**解法**：写完全文后回来对照，确保每个贡献都有实验验证。

### 错误 4：攻击先前工作

```latex
% ❌ 攻击性语言
Previous methods are fundamentally flawed because...
The naive approach of [Author] fails to...

% ✅ 客观分析
While effective in dense-view settings, these methods
face challenges when the number of input views is
limited, as the lack of multi-view correspondence
leads to ambiguous reconstructions.
```

### 错误 5：Figure 1 与文字脱节

Introduction 通常包含一张 Figure 1（方法概览或问题示意图）。这张图必须与 Introduction 的文字紧密配合。

**建议**：在 Introduction 中至少引用 Figure 1 一次，并用文字解释图中展示的核心观点。

---

## 段落衔接范本

以下是各段之间的衔接句型：

### 大背景 → 具体问题
- "Despite this progress, ..."
- "However, a critical limitation remains: ..."
- "While promising, these advances rely on ..."

### 具体问题 → 现有方法不足
- "To address this challenge, prior work has explored ..."
- "Existing approaches to this problem can be categorized into ..."

### 现有方法不足 → 我们的方法
- "In this work, we take a different approach."
- "Our key insight is that ..."
- "Motivated by [observation], we propose ..."

### 我们的方法 → 贡献列表
- "In summary, our contributions are as follows:"
- "Our main contributions include:"
- "To summarize, we make the following contributions:"

---

## 自我检查清单

写完 Introduction 后，回答以下问题：

```
□ 读完第一段，读者能理解这个领域吗？
□ 读完第二段，读者能理解具体问题吗？
□ 读完第三段，读者能理解为什么需要新方法吗？
□ 读完第四段，读者能理解你的核心 idea 吗？
□ 贡献列表的每一条都是具体的、可验证的吗？
□ Figure 1 是否被引用并解释？
□ 段落之间的逻辑衔接是否自然？
□ 是否避免了攻击性语言？
□ 总长度是否控制在 1-1.5 页？
```

---

*回到主文件 → `../SKILL.md`*
