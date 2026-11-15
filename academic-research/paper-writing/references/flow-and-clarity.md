# Flow and Clarity 段落逻辑与文章流畅度

## 核心原则

一篇好论文读起来像在听一个流畅的故事：每一段自然地引出下一段，读者永远不会问「为什么突然在讲这个？」。好的 flow 是看不见的——读者只会觉得「很好懂」而不会意识到你在刻意衔接。坏的 flow 则会让 reviewer 写下 "The paper is hard to follow" 或 "The presentation needs improvement"。

---

## 段落逻辑验证方法

### 方法 1：Topic Sentence 串读法

将每个段落的第一句（topic sentence）单独抽出来，按顺序排列。如果只读这些 topic sentence 就能理解整篇论文的逻辑脉络，说明结构是合理的。

**操作步骤**：

1. 在每段的第一句旁标记 [T1], [T2], [T3]...
2. 将所有 topic sentence 列出来
3. 检查：
   - 相邻的 topic sentence 之间有逻辑关系吗？
   - 整体是否构成一个完整的论述？
   - 有没有逻辑跳跃？

**范例**：

```
[T1] 3D reconstruction from sparse views is important
     for robotics applications.
[T2] However, existing methods require dense input views.
[T3] Prior approaches fall into two categories.
[T4] Regression-based methods struggle with unseen regions.
[T5] Generative approaches produce geometrically
     inconsistent results.
[T6] We observe that coarse geometry provides sufficient
     guidance.
[T7] We propose SparseRecon, a coarse-to-fine framework.
[T8] Our contributions are as follows.
```

上面的 topic sentence 串起来构成了一个完整的 Introduction 逻辑。

### 方法 2：因果链验证法

对每对相邻段落，问一个问题：「为什么读者读完上一段之后，会想读下一段？」

可能的回答（逻辑关系）：

| 关系 | 说明 | 连接词 |
|------|------|--------|
| 因果 | 上段引出问题，下段回答 | Therefore / Thus |
| 转折 | 上段说了一面，下段说另一面 | However / Despite |
| 递进 | 下段深化上段的论点 | Furthermore / Moreover |
| 具体化 | 下段是上段的具体实现 | Specifically / In particular |
| 分支 | 上段提出多面向，下段处理其中一个 | First / Regarding |

如果找不到逻辑关系，说明两段之间存在**逻辑断裂**。

### 方法 3：问答检验法

在每段结尾想像读者会问什么问题，下一段必须回答这个问题：

```
段落 1：3D reconstruction from sparse views is challenging.
         → 读者问：「现有方法怎么做的？」

段落 2：Existing methods fall into regression and generation.
         → 读者问：「这些方法有什么问题？」

段落 3：Both families lack explicit geometric reasoning.
         → 读者问：「那你怎么解决？」

段落 4：Our key insight is that coarse geometry suffices.
         → 读者问：「具体怎么做？」

段落 5：We propose SparseRecon, a coarse-to-fine framework.
         → 读者问：「你的贡献是什么？」

段落 6：Our contributions are: (1)... (2)... (3)...
```

如果某一段没有回答上一段引出的问题，就是逻辑断裂。

---

## Topic Sentence → Support → Transition

每个段落都遵循三部分结构：

### Topic Sentence（主题句）

段落的第一句，宣告本段的核心讯息。

**好的 topic sentence 特征**：
- 可以独立成为一个完整的 claim
- 后续句子都在支撑或展开这个 claim
- 读者读完就知道这段在说什么

```latex
% ✅ 好的 topic sentence
The cost volume provides a robust geometric prior
even under severe occlusion.

% ❌ 坏的 topic sentence（太含糊）
We describe our method in this section.

% ❌ 坏的 topic sentence（太细节）
We set the number of depth hypotheses to 128.
```

### Support（支撑句）

提供证据、解释、或例子来支撑 topic sentence：

| 支撑类型 | 作用 | 范例 |
|---------|------|------|
| 解释 | 说明为什么 topic sentence 是对的 | "This is because the cost volume aggregates information across all view pairs, providing redundancy against single-view failures." |
| 证据 | 用数据支撑 | "As shown in Table 3, removing the cost volume reduces PSNR by 2.4 dB." |
| 例子 | 用具体案例说明 | "For instance, in scene X where 60% of the target view is occluded, ..." |
| 对比 | 与替代方案比较 | "In contrast, monocular depth estimates lack multi-view consistency, leading to artifacts at view boundaries." |

**顺序建议**：解释 → 证据 → 例子 → 对比

### Transition（转换）

段落结尾或下一段开头的衔接，引导读者进入下一个话题：

**转换的位置**：

```
选项 A：在当前段落结尾（段尾转换）
[Topic] [Support] [Support] [Transition → 预告下段]

选项 B：在下一段落开头（段首转换）
[Transition ← 回顾上段] [Topic] [Support] [Support]
```

**段尾转换范例**：
```latex
...the cost volume provides a robust geometric prior.
However, this coarse geometry alone is insufficient for
high-quality rendering, motivating our refinement module
described next.
```

**段首转换范例**：
```latex
While the geometry estimation module provides a strong
structural foundation, the resulting depth maps are too
coarse for photo-realistic rendering. To address this,
we introduce a geometry-conditioned refinement module.
```

---

## 前后文连贯性检查

### 检查 1：术语一致性

全文对同一概念必须使用同一术语：

```
❌ 混用（读者会困惑这是否是不同的东西）
- 段落 1 用 "feature representation"
- 段落 3 用 "feature embedding"
- 段落 5 用 "latent code"

✅ 统一
- 全文统一用 "feature representation"
- 首次出现时定义："feature representation
  (i.e., the output of the encoder)"
```

**检查方法**：搜寻论文中所有指代同一概念的词汇，确保一致。

### 检查 2：逻辑前后不矛盾

```
❌ 矛盾
- Introduction: "Our method requires no additional
  supervision beyond RGB images."
- Method: "We use ground-truth depth for training the
  geometry module."

✅ 一致
- Introduction: "Our method leverages only RGB images
  and coarse depth estimates at training time."
- Method: "During training, we use pseudo ground-truth
  depth from a pretrained stereo model."
```

**检查方法**：列出所有 claim，逐一对照实验和方法的描述。

### 检查 3：数字一致

```
❌ 数字不一致
- Abstract: "improves by 2.3 dB"
- Experiments: Table 1 显示改进了 2.29 dB
- Conclusion: "gains of 2.5 dB"

✅ 一致
- 全文统一使用 "2.3 dB"（可以在表格中显示精确值 2.29）
```

### 检查 4：引用前后呼应

在 Introduction 中提到的问题/方法，必须在后文中有对应：

| Introduction 提到 | 必须在后文出现 |
|------------------|--------------|
| 问题 X 很重要 | Experiments 中解决 X 的实验 |
| 现有方法的缺陷 Y | Method 中描述如何克服 Y |
| 贡献 Z | Method 中 Z 的详细描述 + Experiments 中 Z 的实验验证 |

---

## 常见逻辑断裂模式

### 模式 1：跳跃式论述

```
段落 1：我们的方法使用 cost volume 估计几何。
段落 2：表 3 显示我们的方法在 DTU 上达到 25.4 dB。

问题：从方法描述直接跳到结果，没有过渡。

修正：在两段之间加入「实验设定」或「我们验证 cost volume
的有效性」的过渡段落。
```

### 模式 2：无头段落

```
段落：Additionally, we apply batch normalization after
each convolutional layer. The kernel size is set to 3.
We use ReLU activation.

问题：这段没有 topic sentence，读者不知道为什么要
读这些细节。

修正：加入 topic sentence —— "To stabilize training and
improve convergence, we adopt standard architectural
design choices for the feature extractor:"
```

### 模式 3：回力镖

```
段落 1：介绍方法 A
段落 2：介绍方法 B
段落 3：又回来补充方法 A 的细节

问题：读者读到段落 3 时已经在想方法 B 了，
突然被拉回方法 A 会很困惑。

修正：把方法 A 的所有内容集中在一起。
```

### 模式 4：假设读者有超能力

```
"As discussed earlier, ..."（但之前没有讨论过）
"It is well known that ..."（对你来说 well known，
对读者不一定）
"Following standard practice, ..."（什么 standard？引用？）

修正：加入具体引用或回指（"As shown in Eq. (3), ..."
或 "Following the protocol of [ref], ..."）
```

### 模式 5：不对称的结构

```
3.1 Module A（2 页详细描述）
3.2 Module B（3 行带过）
3.3 Module C（1.5 页详细描述）

问题：如果 Module B 很重要，描述太短让人怀疑完整性。
如果不重要，为什么要单独一个 subsection？

修正：要嘛扩充 Module B 的描述，要嘛将其合并到
其他 subsection 中。
```

---

## Section 间的逻辑流

### Introduction → Related Work

Introduction 末尾的贡献列表自然引出 "在描述方法细节前，我们先回顾相关工作"：

```latex
% Introduction 结尾
...our contributions are: (1)... (2)... (3)...

% Related Work 开头
Before describing our approach in detail, we review
the most relevant prior work in three areas: ...
```

### Related Work → Method

Related Work 末尾指出 gap，Method 开头填补这个 gap：

```latex
% Related Work 结尾
...existing methods either [限制A] or [限制B]. Our
approach addresses both limitations through a unified
framework.

% Method 开头
We now describe our proposed framework that overcomes
the limitations outlined above.
```

### Method → Experiments

Method 末尾可以预告实验，Experiments 开头回顾要验证什么：

```latex
% Method 结尾
[损失函数描述]... The training procedure is summarized
in Algorithm 1.

% Experiments 开头
We evaluate our method on three benchmarks to answer
the following questions: (1) Does SparseRecon outperform
existing sparse-view methods? (2) How important is each
component? (3) How does performance scale with the
number of input views?
```

### Experiments → Conclusion

Experiments 末尾的分析自然引出结论中的总结和限制讨论。

---

## 实用工具

### 连贯性自检表

在完成论文初稿后，逐项检查：

```
□ 所有 topic sentence 串读起来构成完整论述？
□ 相邻段落之间都有明确的逻辑关系？
□ 没有逻辑跳跃（每一步都有铺陈）？
□ 没有回力镖（同一主题的内容集中在一起）？
□ 术语全文一致？
□ 数字全文一致？
□ 所有 claim 都有前后呼应（提出→论证→验证）？
□ Section 之间的衔接自然？
□ 没有假设读者有超能力的地方？
□ 结构对称（类似组件用类似篇幅描述）？
```

### 快速修复策略

| 问题 | 快速修复 |
|------|---------|
| 逻辑跳跃 | 加一个衔接句或一个短段落 |
| 无头段落 | 加 topic sentence |
| 回力镖 | 重新组织段落顺序 |
| 术语不一致 | 全文搜寻替换 |
| 结构不对称 | 扩充短的 or 精简长的 |

---

*回到主文件 → `../SKILL.md`*
