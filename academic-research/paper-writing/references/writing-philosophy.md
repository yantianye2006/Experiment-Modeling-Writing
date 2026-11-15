# Writing Philosophy 写作铁律与禁忌

## 核心信念

学术论文不是文学作品，也不是行销文案。它的唯一目的是**精确、高效地传递资讯**。每一个字都必须服务于这个目的。多余的字不是装饰，是噪音。

---

## 30 秒法则

### 原理

学术 reviewer 每年审数十篇到上百篇论文。他们没有时间仔细读每一个字。研究显示，reviewer 在前 30 秒内就会形成对论文的初步印象，而这个印象对最终评分有巨大影响。

### 30 秒内 reviewer 看的东西

按优先顺序排列：

1. **标题**（5 秒）
   - 能否立即理解这篇论文在做什么？
   - 是否有新颖的关键词吸引注意？

2. **摘要**（10 秒）
   - 前两句能否理解问题和方法？
   - 最后一句有没有数字结果？

3. **Figure 1**（10 秒）
   - 能否直觉理解方法的核心？
   - 图的品质是否专业？

4. **Table 1 / 主结果**（5 秒）
   - 有没有加粗的最佳结果？
   - 改进幅度明显吗？

### 实践方法

#### 标题优化

```
❌ 模糊标题
A Deep Learning Approach for 3D Reconstruction

❌ 太长的标题
A Novel Coarse-to-Fine Neural Implicit Representation
Framework with Geometric Guidance for High-Quality
Sparse-View 3D Scene Reconstruction

✅ 清晰、适中的标题
SparseRecon: Geometry-Guided Neural Reconstruction
from Sparse Views
```

**标题公式**：[方法名称]: [核心技术] for [目标任务]

#### 摘要前两句优化

```
❌ 前两句还在讲背景
Deep learning has revolutionized computer vision.
3D reconstruction is an important task.

✅ 前两句直奔主题
Reconstructing 3D scenes from sparse views remains
challenging due to insufficient multi-view overlap.
We present SparseRecon, a coarse-to-fine framework
that leverages explicit geometric priors to guide
neural reconstruction.
```

#### Figure 1 优化

- 必须是**自解释的**——不看正文也能理解
- 字体要足够大（列印后仍可读）
- 标注要清楚（输入→处理→输出的流向）
- 如果是结果对比图，要有明显的视觉差异

#### Table 1 优化

- 最佳结果加粗，一眼可见
- 你的方法在最后一行，用 `\midrule` 分隔
- 改进幅度最好 > 1%（否则 reviewer 不会印象深刻）

---

## 禁用词汇完整清单

### 绝对禁止

这些词在任何情况下都不应该出现在学术论文中：

| 禁用词 | 问题 | 替代 |
|--------|------|------|
| novel | 过度使用，已失去意义 | we propose / we introduce / we present |
| groundbreaking | 夸大 | effective / promising / competitive |
| revolutionize | 夸大 | improve / advance / enable |
| dramatically | 夸大 | significantly / substantially / by X% |
| obviously | 傲慢 | (直接陈述事实) |
| clearly | 可能不 clear | As shown in Fig. X / Table X shows |
| very / really | 空洞 | (用具体数字代替) |
| of course | 傲慢 | (直接陈述事实) |
| trivially | 对读者不友善 | straightforwardly / directly |
| interestingly | 主观 | notably / we observe that |
| unfortunately | 不必要的情感 | however / a limitation is |
| believe | 主观 | hypothesize / expect / observe |

### 谨慎使用

以下词汇不是完全禁止，但需要明确的支持证据：

| 词汇 | 使用条件 |
|------|---------|
| state-of-the-art | 只在你确实超越所有现有方法时 |
| significant | 只在有统计检验支持时 |
| outperform | 只在有具体数字时 |
| superior | 只在有多个指标支持时 |
| robust | 只在有跨条件实验支持时 |
| efficient | 只在有效率数据（FLOPs、时间）支持时 |
| generalize | 只在有跨资料集实验支持时 |
| scalable | 只在有 scaling 实验支持时 |

### 推荐的学术用语

| 场景 | 推荐用语 |
|------|---------|
| 提出方法 | We propose / present / introduce |
| 描述结果 | achieves / attains / yields |
| 比较优势 | improves over / outperforms ... by X |
| 观察现象 | We observe that / We find that |
| 分析原因 | This is because / We attribute this to |
| 假设 | We hypothesize that / We conjecture that |
| 承认限制 | A limitation of our approach is / Our method may struggle with |

---

## 段落结构规则

### 规则 1：Topic Sentence 开头

每个段落的第一句必须是 topic sentence，概括本段的核心讯息：

```latex
% ✅ 清晰的 topic sentence
The geometry estimation module is the cornerstone of
our framework. [接下来解释为什么...]

% ❌ 没有 topic sentence
We first extract features using a CNN. Then we compute
a cost volume. After that, we apply regularization...
% [读者不知道这段在说什么]
```

### 规则 2：一段一讯息

每个段落只传递一个核心讯息。检验方法：如果你能用一句话概括这个段落，就是好的；如果需要两句以上，就要拆分。

```
❌ 一段包含两个讯息
Our geometry module estimates depth maps. [细节...]
Additionally, we found that data augmentation significantly
improves generalization. [细节...]

✅ 拆成两段
[段落 1] Our geometry module estimates depth maps. [细节...]

[段落 2] To improve generalization, we apply data
augmentation during training. [细节...]
```

### 规则 3：段落长度

- **最佳**：4-8 句
- **可接受**：3-10 句
- **太短**：1-2 句（通常可以合并到相邻段落）
- **太长**：超过 10 句（必须拆分）

### 规则 4：段落间转换

相邻段落之间必须有逻辑衔接。常用的转换方式：

| 转换类型 | 范例 |
|---------|------|
| 因果 | Therefore / As a result / Consequently |
| 对比 | However / In contrast / On the other hand |
| 递进 | Furthermore / Moreover / In addition |
| 具体化 | Specifically / In particular / More concretely |
| 总结 | In summary / Overall / To summarize |
| 时间 | First / Then / Finally |

---

## 句子层面的写作原则

### 原则 1：主动语态优先

```latex
% ❌ 被动（弱）
The features are extracted by the encoder.

% ✅ 主动（强）
The encoder extracts features from the input image.
```

例外：描述普遍做法时可以用被动（"X is widely used in ..."）

### 原则 2：避免长句

如果一个句子超过 30 个字，考虑拆分：

```latex
% ❌ 太长
We propose a method that first estimates coarse geometry
using a cost volume constructed from multi-view feature
correlations and then refines the reconstruction through
a neural implicit representation conditioned on the
geometry-aware features extracted from the input views.

% ✅ 拆分
We first estimate coarse geometry using a cost volume
built from multi-view feature correlations. We then
refine the reconstruction through a neural implicit
representation, conditioned on geometry-aware features
from the input views.
```

### 原则 3：平行结构

列举时保持语法结构一致：

```latex
% ❌ 不平行
Our method (1) estimates geometry, (2) extraction of
features, and (3) rendering novel views.

% ✅ 平行
Our method (1) estimates geometry, (2) extracts features,
and (3) renders novel views.
```

### 原则 4：避免模糊指代

```latex
% ❌ 模糊的 "this"
We compute the cost volume and regularize it. This
improves the result significantly.
% [读者不知道 "This" 指什么：计算、正则化、还是两者？]

% ✅ 明确指代
We compute the cost volume and regularize it. This
regularization step improves reconstruction quality
by 1.5 dB.
```

---

## 常见语法错误

| 错误 | 范例 | 修正 |
|------|------|------|
| 冠词缺失 | "We use network to..." | "We use **a** network to..." |
| 主词动词不一致 | "The results shows..." | "The results show..." |
| 悬吊修饰 | "Using our method, the results improved." | "Using our method, **we** improved the results." |
| 逗号拼接 | "We train the model, it converges in 10 epochs." | "We train the model**;** it converges in 10 epochs." |
| that/which 混用 | 限定用 which | 限定用 **that**，非限定用 **which** |

---

## 自我编辑流程

写完每个段落后，依序问自己：

```
1. 这段的 topic sentence 是什么？
2. 每一句都服务于这个 topic 吗？
3. 有没有句子可以删除而不影响理解？
4. 有没有使用禁用词汇？
5. 有没有超过 30 字的长句？
6. 与上下段的衔接是否自然？
```

如果答案有任何一个「否」，就需要修改。

---

*回到主文件 → `../SKILL.md`*
