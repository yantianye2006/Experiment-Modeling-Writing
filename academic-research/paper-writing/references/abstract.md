# Abstract 摘要写作指南

## 核心原则

摘要是整篇论文的缩影。Reviewer 读完摘要后，对你的论文已经有了 70% 的判断。一个好的摘要必须在 150-250 字内回答四个问题。

---

## 4 句话结构

每篇顶级会议论文的摘要都可以拆解为以下四个部分（不一定恰好各一句，但逻辑上必须涵盖）：

### 第 1 部分：问题（Problem）

- **目标**：告诉读者你在解决什么问题，以及为什么这个问题重要
- **长度**：1-2 句
- **要点**：
  - 问题本身必须是大家认同的、有价值的
  - 避免过于狭窄（"We address the task of predicting X on dataset Y"）
  - 从更高的角度切入（"Understanding 3D scenes from limited observations remains a fundamental challenge in ..."）

**范例**：
```latex
% 好的问题陈述
Reconstructing high-fidelity 3D scenes from sparse observations
is essential for applications in robotics and augmented reality,
yet remains challenging due to the inherent ambiguity of
under-constrained views.

% 坏的问题陈述（太狭窄）
We study the problem of novel view synthesis on the DTU dataset.
```

### 第 2 部分：方法（Approach）

- **目标**：用一句话概括你的核心方法思路
- **长度**：1-2 句
- **要点**：
  - 不要讲技术细节，讲核心 idea
  - 强调「为什么你的方法能解决上述问题」
  - 使用 "We propose / We present / We introduce" 开头

**范例**：
```latex
% 好的方法描述
We present SparseRecon, a coarse-to-fine framework that first
estimates a rough geometry proxy from available views, then
progressively refines it through a learned neural implicit
representation conditioned on local features.

% 坏的方法描述（太含糊）
We propose a novel deep learning method for this task.

% 坏的方法描述（太详细）
We use a ResNet-50 backbone followed by three transformer layers
with 8 attention heads and a hidden dimension of 512...
```

### 第 3 部分：结果（Results）

- **目标**：用具体数字展示你的方法的效果
- **长度**：1-2 句
- **要点**：
  - 必须有具体数字（百分比、提升幅度）
  - 提及你在哪些 benchmark 上做了实验
  - 与 SOTA 做明确比较

**范例**：
```latex
% 好的结果描述
Extensive experiments on three standard benchmarks (DTU, BlendedMVS,
and Tanks\&Temples) demonstrate that SparseRecon outperforms
existing methods by 2.3 dB PSNR on average while requiring
only 3 input views, compared to 10+ views for prior approaches.

% 坏的结果描述（没有数字）
Experiments show that our method achieves superior performance
compared to existing approaches.
```

### 第 4 部分：影响（Impact / Takeaway）

- **目标**：告诉读者这个工作的更广泛意义或启示
- **长度**：1 句
- **要点**：
  - 这部分是可选的，但有的话会让摘要更完整
  - 可以提到开源计划、更广泛的适用性、或揭示的 insight
  - 不要过度宣称

**范例**：
```latex
% 好的影响描述
Our results suggest that explicit geometric reasoning,
even at a coarse level, provides a strong inductive bias
that significantly reduces the view requirements for
high-quality reconstruction.

% 坏的影响描述（过度宣称）
Our method will revolutionize the field of 3D reconstruction.
```

---

## 长度建议

| 会议 | 建议字数 | 备注 |
|------|---------|------|
| NeurIPS | 150-200 字 | 简洁为上 |
| ICLR | 150-250 字 | 可以稍长 |
| CVPR/ECCV | 150-200 字 | 通常较短 |
| ACL | 200-250 字 | NLP 论文摘要稍长 |
| AAAI | 150 字 | 版面限制严格 |

**黄金法则**：如果你的摘要超过 250 字，几乎一定可以删减。

---

## 常见错误

### 错误 1：缺少具体数字

```latex
% ❌ 没有数字的摘要
Our method achieves state-of-the-art performance on multiple
benchmarks, significantly outperforming existing methods.

% ✅ 有数字的摘要
Our method achieves 78.3% mAP on COCO, outperforming the
previous best (75.1%) by 3.2 points, while using 40% fewer
parameters.
```

### 错误 2：背景太长

```latex
% ❌ 背景占了摘要一半
Deep learning has achieved remarkable progress in computer vision.
Convolutional neural networks have been widely adopted for image
classification, object detection, and semantic segmentation.
Recently, transformer architectures have shown promising results...
[然后才开始说自己的方法]

% ✅ 直奔主题
Semantic segmentation in low-resource settings remains challenging
as existing methods require large-scale pixel-level annotations.
We propose...
```

### 错误 3：使用禁用词汇

```latex
% ❌ 花俏词汇
We propose a novel and groundbreaking framework that dramatically
revolutionizes the field of...

% ✅ 平实描述
We propose a framework that addresses [specific problem] by
[specific technique], achieving [specific result].
```

### 错误 4：没有提到问题的重要性

```latex
% ❌ 直接说方法，不说为什么
We propose a new method for X. Our method uses A and B.

% ✅ 先说为什么再说方法
X is critical for [application] but existing methods suffer
from [limitation]. We propose a new method that addresses
this by [approach].
```

### 错误 5：过度压缩方法描述

```latex
% ❌ 方法描述太含糊
We use a learning-based approach.

% ✅ 清楚说明核心 idea
We introduce a two-stage approach: first learning a geometric
prior from synthetic data, then adapting it to real scenes
through a self-supervised refinement module.
```

---

## 完整好范例

```latex
\begin{abstract}
Generating realistic human motions from text descriptions enables
numerous applications in animation, gaming, and virtual reality,
yet remains challenging due to the complexity of human dynamics
and the ambiguity of natural language.  % [问题]
%
We present MotionCraft, a diffusion-based framework that decomposes
the text-to-motion generation into semantic planning and motion
synthesis stages, where the planner first extracts structured
action primitives from text, and the synthesizer generates
temporally coherent motions conditioned on these primitives.  % [方法]
%
On the HumanML3D and KIT-ML benchmarks, MotionCraft achieves
an FID of 0.141 and 0.532 respectively, improving over the
previous state-of-the-art by 18.5\% and 12.3\%, while
producing motions rated 4.2/5.0 in human perceptual studies. % [结果]
%
Our analysis reveals that explicit semantic decomposition not
only improves generation quality but also provides interpretable
control over the generation process.  % [影响]
\end{abstract}
```

---

## 写作流程建议

1. **最后写**：摘要应该在全文完成后才写，这样你最清楚论文的核心贡献
2. **先写长版**：先不管字数限制，把想说的都写下来
3. **删减到目标字数**：每一句都问「这句必要吗？」
4. **请他人阅读**：找一个不熟悉你工作的人读摘要，看他们能否理解
5. **对照 4 句话结构**：确认四个部分都有涵盖

---

*回到主文件 → `../SKILL.md`*
