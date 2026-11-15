# Related Work 相关工作写作指南

## 核心原则

Related Work 不是文献列表。它的目的是帮助读者理解你的工作在研究版图中的位置，以及你与先前工作的本质差异。写得好的 Related Work 会让 reviewer 觉得你对领域有深刻理解；写得差的会让他们觉得你只是在凑引用。

---

## 组织方式

### 方式 A：按主题分组（推荐）

将相关工作按照**技术主题**或**方法类别**分组，每组一个 subsection 或一个段落。

**优点**：
- 结构清晰，读者容易找到感兴趣的部分
- 自然引出你的方法与每组方法的差异
- 便于 reviewer 检查你是否遗漏重要引用

**组织范例**：

```
3.1 Neural Implicit Representations
    [讨论 NeRF 系列工作]

3.2 Sparse-View Reconstruction
    [讨论稀疏视角重建工作]

3.3 Geometric Priors for 3D Reconstruction
    [讨论几何先验工作]
```

**每个分组的结构**：

```latex
% 分组标题
\paragraph{Neural Implicit Representations.}
% 1. 简述这个方向的起源和核心思想（1-2句）
Neural radiance fields (NeRF)~\cite{nerf} represent scenes
as continuous functions mapping 3D coordinates to color
and density, enabling photorealistic novel view synthesis.
% 2. 介绍主要进展（2-3句，引用关键论文）
Subsequent works have improved training
efficiency~\cite{instant_ngp,plenoxels}, generalization to
new scenes~\cite{pixelnerf,ibrnet}, and quality through
better regularization~\cite{mipnerf,regnerf}.
% 3. 指出与你的方法的关联和差异（1-2句）★关键★
While these methods have advanced dense-view reconstruction,
they require substantial multi-view overlap. Our work builds
on the implicit representation framework but introduces
explicit geometric guidance to enable reconstruction from
as few as three views.
```

### 方式 B：按时间线（不推荐，但某些情况可用）

按时间顺序介绍相关工作的发展脉络。

**适用情境**：
- 综述型论文
- 你的方法是某个研究脉络的自然延伸
- 需要展示领域演进历程

**风险**：容易写成流水帐，缺乏深度分析。

### 方式 C：按问题维度（适用于多面向问题）

如果你的问题涉及多个面向，可以按面向分组。

**范例**（文字生成运动）：
```
3.1 Text Understanding for Motion
3.2 Motion Generation Models
3.3 Motion Quality Evaluation
```

---

## 差异化比较

Related Work 的核心价值在于差异化比较。每组相关工作的结尾必须说明你的方法与它们的**本质差异**。

### 差异化句型

```latex
% 强调不同的出发点
Unlike [方向A] which addresses X from the perspective of Y,
our work approaches it through Z.

% 强调不同的假设
While [方法A] assumes [假设], our method relaxes this
constraint by [做法].

% 强调不同的技术路线
In contrast to [方法A] that relies on [技术],
we leverage [不同技术] to achieve [效果].

% 强调互补关系
Our work is complementary to [方向A]; while they focus
on [面向], we address the orthogonal challenge of [面向].

% 强调改进
Building upon [方法A], our approach further improves
[面向] by introducing [新元素].
```

### 好的差异化 vs 坏的差异化

```latex
% ❌ 没有实质差异化（空洞）
Our method is different from previous methods.

% ❌ 只是说「我们更好」
Our method outperforms all previous methods.

% ❌ 攻击性语言
Previous methods are naive and ineffective.

% ✅ 具体的技术差异
Unlike PixelNeRF~\cite{pixelnerf} which predicts features
independently for each view, our method explicitly models
inter-view geometric consistency through a cost volume,
enabling more coherent reconstruction in overlapping regions.

% ✅ 互补角度
Our work is most related to RegNeRF~\cite{regnerf}, which
also addresses sparse-view reconstruction. While RegNeRF
regularizes geometry through rendered patch supervision,
our approach provides direct geometric guidance through
an estimated depth proxy. These strategies are complementary,
and we show in Sec.~\ref{sec:ablation} that combining them
yields further improvements.
```

---

## 避免变成文献列表

### 文献列表 vs 有分析的 Related Work

```latex
% ❌ 文献列表（每篇论文一句话，没有分析）
[A]~\cite{a} proposed X. [B]~\cite{b} introduced Y.
[C]~\cite{c} presented Z. [D]~\cite{d} developed W.

% ✅ 有分析的 Related Work（有归纳、有比较）
A family of methods~\cite{a,b,c} addresses X through the
shared strategy of Y. Among them, [A]~\cite{a} focuses on
[面向1], while [B]~\cite{b} extends this to [面向2].
A notable limitation of this approach is [限制], which
[D]~\cite{d} partially addresses through [方法] but at the
cost of [代价]. Our method avoids this trade-off entirely
by [做法].
```

### 分析的维度

对每组相关工作，可以从以下维度进行分析：

| 维度 | 问题 |
|------|------|
| 假设 | 这组方法做了什么假设？这些假设合理吗？ |
| 能力 | 这组方法能做什么？不能做什么？ |
| 代价 | 达成效果的代价是什么？（计算量、资料需求等） |
| 限制 | 在什么场景下会失效？ |
| 与本文关系 | 本文的方法如何克服这些限制？ |

---

## 引用数量建议

| 会议 | 建议引用数 | Related Work 长度 |
|------|----------|-----------------|
| NeurIPS/ICML | 30-50 | 0.5-1 页 |
| ICLR | 30-50 | 0.5-1 页 |
| CVPR/ECCV | 40-60 | 0.5-1 页 |
| ACL/EMNLP | 30-50 | 0.75-1 页 |

### 引用策略

- **必须引用**：直接相关的工作（方法类似或问题相同）
- **应该引用**：同一方向的重要里程碑论文
- **可以引用**：相关但不同方向的背景知识
- **避免引用**：与你的工作完全无关的论文（灌引用会被 reviewer 看出来）

### Reviewer 常见的引用相关质疑

- "The authors missed important related work: [X]" → 确保覆盖所有主要方向
- "The comparison with [X] is missing" → 在 Related Work 和 Experiments 中都要有
- "The distinction from [X] is unclear" → 每组相关工作结尾必须有差异化

---

## 位置选择

Related Work 的位置有两种常见选择：

### 选项 1：Introduction 之后（Section 2）

- **适用**：Related Work 为后续 Method 提供必要背景知识
- **优点**：读者有足够背景理解你的方法
- **常见于**：大多数论文

### 选项 2：Experiments 之后

- **适用**：Method 不需要太多背景知识就能理解
- **优点**：读者更快看到你的技术贡献
- **常见于**：NeurIPS 部分论文、方法非常直觉的论文

**建议**：除非有特殊理由，预设放在 Introduction 之后。

---

## 自我检查清单

```
□ 是否按主题分组而非逐篇列举？
□ 每个分组是否有 2 句以上的分析（而非只是列举）？
□ 每个分组结尾是否说明了与本文的差异？
□ 是否覆盖了所有 reviewer 可能想到的相关方向？
□ 是否引用了最新的相关论文（近 1-2 年）？
□ 是否避免了攻击性语言？
□ 总长度是否控制在 0.5-1 页？
□ 引用格式是否统一且正确？
```

---

*回到主文件 → `../SKILL.md`*
