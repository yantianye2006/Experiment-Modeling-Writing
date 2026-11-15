---
name: paper-review
description: "学术论文审稿技能 — 以结构化四步骤流程完成深度论文审查，涵盖批判性审查、分数预测、要点精炼与正式审稿产出。当使用者需要 review 一篇论文、模拟 reviewer 反应、评估论文能否被接收、或帮助判断论文优缺点时，一定要使用此技能。触发词包括：review 这篇、帮我审稿、reviewer 会怎么说、这篇能上吗、paper review、给分数、找 weakness。适用于任何学术论文的审稿模拟与评估。"
license: MIT
compatibility: Works with Claude Code, ChatGPT/Codex CLI, and Gemini CLI.
metadata:
  author: weed
  version: "1.0.0"
---

# paper-review：学术论文审稿技能

## 概述

本技能提供一套系统化的学术论文审稿流程，适用于顶级会议（如 NeurIPS、ICML、ICLR、ACL、CVPR 等）与期刊的同侪审查。整个流程分为四个步骤，前三步以简体中文进行深度分析，第四步默认产出简体中文正式审稿；用户明确要求英文时，再输出符合会议格式的英文审稿。

### 核心理念

- **严谨但公平**：审稿的目的是提升学术品质，而非打压作者
- **具体而非模糊**：所有批评都应指向具体段落、公式或实验
- **建设性导向**：指出问题的同时提供改进方向
- **多维度评估**：不以单一标准论断，全面考量论文各面向

---

## 四步骤审稿流程

### 总览

| 步骤 | 名称 | 语言 | 目的 |
|------|------|------|------|
| Step 1 | 批判性审查 | 简体中文 | 深入阅读，找出优缺点 |
| Step 2 | 分数预测 | 简体中文 | 各维度评分与整体分数预测 |
| Step 3 | 要点精炼 | 简体中文 | 将发现整理为结构化要点 |
| Step 4 | 正式审稿 | 简体中文 | 产出结构完整的正式 review；用户明确要求时可改用英文 |

---

### Step 1：批判性审查（简体中文）

#### 目标

以批判性思维深入阅读论文，系统性地识别优点与缺点。此步骤为后续所有分析的基础。

#### 执行方式

1. **第一遍：快速浏览（5 分钟思维）**
   - 阅读标题、摘要、导论、结论
   - 浏览图表与表格
   - 形成初步印象：这篇论文在做什么？声称了什么贡献？

2. **第二遍：仔细阅读（30 分钟思维）**
   - 逐节阅读，标记不清楚的地方
   - 检查数学推导的正确性
   - 验证实验设置的合理性
   - 确认 claims 是否有充分支持

3. **第三遍：批判性分析（15 分钟思维）**
   - 对照五大审查维度逐一评估
   - 识别是否符合五大退稿模式
   - 思考 missing baselines、missing ablations、missing analysis

#### 输出格式

```
## Step 1：批判性审查

### 论文基本资讯
- 标题：
- 作者：
- 投稿会议/期刊：
- 领域：

### 初步印象
（一段话总结论文做了什么、声称了什么）

### 优点列表
1. [S1] （具体描述优点，引用论文段落或页码）
2. [S2] ...

### 缺点列表
1. [W1] （具体描述缺点，说明为什么这是问题）
2. [W2] ...

### 疑问列表
1. [Q1] （需要作者厘清的问题）
2. [Q2] ...

### 初步判断
（对论文品质的初步判断，包含是否达到会议门槛的直觉）
```

#### 注意事项

- 优点和缺点都要具体，避免「写得不错」「实验不足」这类空泛评语
- 每个优缺点都应该能对应到论文的具体位置
- 疑问列表要区分「真正的疑问」与「修辞性的批评」
- 初步判断只是直觉，不要被它锚定——后续步骤可能改变结论

---

### Step 2：分数预测（简体中文）

#### 目标

基于 Step 1 的分析，对论文的五个维度分别评分，并预测整体分数。

#### 五大审查维度

每个维度以 1-5 分评分。详细评分标准见 `references/scoring-rubric.md`。

| 维度 | 说明 | 权重参考 |
|------|------|----------|
| 贡献新颖性 (Novelty & Contribution) | 想法是否新颖？贡献是否足够？ | 高 |
| 写作清晰度 (Clarity & Writing) | 论文是否易读？逻辑是否清晰？ | 中 |
| 实验严谨性 (Experimental Rigor) | 实验设计是否严谨？结果是否可靠？ | 高 |
| 评估完整性 (Evaluation Completeness) | 评估是否全面？是否有遗漏的比较？ | 中高 |
| 方法健全性 (Soundness of Method) | 方法是否正确？假设是否合理？ | 高 |

详细的维度说明请参考 `references/review-dimensions.md`。

#### 评分体系

- **Overall Score（整体分数）**：1-10 分，详见 `references/scoring-rubric.md`
- **Confidence（信心度）**：1-5 分，反映审稿者对自身评估的确信程度
- **各维度分数**：1-5 分

#### 输出格式

```
## Step 2：分数预测

### 各维度评分

| 维度 | 分数 (1-5) | 简要理由 |
|------|-----------|----------|
| 贡献新颖性 | X | （一句话理由） |
| 写作清晰度 | X | （一句话理由） |
| 实验严谨性 | X | （一句话理由） |
| 评估完整性 | X | （一句话理由） |
| 方法健全性 | X | （一句话理由） |

### 整体分数预测
- **Overall Score**: X / 10
- **Confidence**: X / 5

### 分数推理
（解释为什么给这个整体分数，各维度如何影响最终判断）

### 与接受门槛的比较
（讨论这篇论文相对于目标会议的接受门槛如何，是 clear accept、borderline 还是 clear reject）
```

#### 注意事项

- 各维度分数应与 Step 1 的优缺点一致
- 整体分数不是各维度的简单平均——有些致命缺陷会直接拉低整体分数
- Confidence 要诚实——如果你不熟悉这个子领域，信心度应该较低
- 考虑会议的接受率（如 NeurIPS ~25%、ICML ~25%、workshop ~50%）

---

### Step 3：要点精炼（简体中文）

#### 目标

将 Step 1 和 Step 2 的分析整理为精炼的结构化要点，作为 Step 4 正式审稿的草稿。

#### 执行方式

1. **合并与去重**：将 Step 1 的优缺点合并，去除重复
2. **排序**：按重要性排序，最重要的放最前面
3. **补充细节**：为每个要点补充具体的论文引用与建议
4. **分类**：区分 major concerns 和 minor concerns
5. **撰写建议**：为每个缺点提供具体的改进建议

#### 输出格式

```
## Step 3：要点精炼

### 核心优点（按重要性排序）
1. [Major S1] （精炼描述 + 论文引用）
2. [Major S2] ...

### 重大问题（Major Concerns）
1. [Major W1] （精炼描述 + 为什么重要 + 建议改进方向）
2. [Major W2] ...

### 次要问题（Minor Concerns）
1. [Minor W1] （精炼描述 + 建议改进方向）
2. [Minor W2] ...

### 必问问题（Questions for Authors）
1. [Q1] （精炼问题 + 为什么这个答案很重要）
2. [Q2] ...

### 一句话总结
（用一句话总结对这篇论文的评价）
```

#### 注意事项

- Major 和 Minor 的区分要明确——Major 是会影响接受与否的问题
- 每个缺点都应该附带建议，体现建设性审稿精神
- 问题要有策略性——好的问题能帮助你在 rebuttal 后做出更好的判断
- 建设性回馈的写法请参考 `references/constructive-feedback.md`

---

### Step 4：正式审稿（默认简体中文）

#### 目标

基于前三步的简中分析，默认产出结构完整的简体中文正式 review；用户明确要求英文时再切换。

#### 执行方式

1. 使用 `templates/review-form.md` 中的模板
2. 将 Step 3 的要点整理并润饰为专业、清晰的简体中文；用户明确要求英文时再翻译
3. 确保语气专业、客观、建设性
4. 检查是否遗漏了重要的优缺点

#### 正式审稿结构

```
## Summary
（2-4 句话总结论文的主要贡献与方法）

## Strengths
1. [S1] ...
2. [S2] ...

## Weaknesses
1. [W1] ...
2. [W2] ...

## Questions for Authors
1. [Q1] ...
2. [Q2] ...

## Suggestions for Improvement
1. ...
2. ...

## Minor Issues
- （格式、typo、文法等小问题）

## Rating
- Overall: X/10
- Confidence: X/5

## Justification
（简短解释你的评分理由）
```

#### 语气指引

- **避免**：「This paper is bad.」「The authors clearly don't understand...」
- **推荐**：「The paper would benefit from...」「It is unclear how...」「A potential concern is...」
- 使用学术审稿的惯用语（参考 `references/constructive-feedback.md`）
- 批评要对事不对人——评论论文，不评论作者

#### 注意事项

- Summary 要准确反映论文内容，让作者知道你确实读了论文
- Strengths 要真诚——即使你要拒稿，也要承认论文的优点
- Weaknesses 要具体——指出具体的段落、公式、实验
- Questions 要有策略性——能帮助你在 rebuttal 后做决定
- 退稿模式的参考请见 `references/rejection-patterns.md`

---

## 五大审查维度（详细版）

以下为五大审查维度的摘要。完整说明请参考 `references/review-dimensions.md`。

### 1. 贡献新颖性 (Novelty & Contribution)

- 这个想法之前有人做过吗？
- 贡献的量和质是否足以支撑一篇完整论文？
- 相对于 prior work，增量有多大？
- 是技术新颖、应用新颖，还是视角新颖？

### 2. 写作清晰度 (Clarity & Writing)

- 非专家能否理解论文的主要贡献？
- 动机是否清晰？为什么这个问题重要？
- 符号和术语是否一致？
- 图表是否清晰且有助理解？

### 3. 实验严谨性 (Experimental Rigor)

- 实验设计是否足以验证 claims？
- 是否有适当的 baselines？
- 是否报告了统计显著性或误差范围？
- 超参数选择是否合理？是否进行了公平比较？

### 4. 评估完整性 (Evaluation Completeness)

- 资料集是否足够多样？
- 是否有 ablation study？
- 是否有分析（error analysis、case study）？
- 是否讨论了局限性？

### 5. 方法健全性 (Soundness of Method)

- 数学推导是否正确？
- 假设是否合理且被明确陈述？
- 方法是否能如声称般运作？
- 是否有理论保证或直觉性解释？

---

## 五大退稿模式

以下为五大退稿模式的摘要。完整说明与范例请参考 `references/rejection-patterns.md`。

### 模式 1：贡献不足 (Insufficient Contribution)

- 症状：增量改进、trivial extension、已知结果的简单组合
- 典型触发语：「This is a straightforward extension of [X].」

### 模式 2：不清楚 (Lack of Clarity)

- 症状：读不懂、逻辑跳跃、符号混乱、缺少直觉
- 典型触发语：「The paper is difficult to follow.」

### 模式 3：效果弱 (Weak Results)

- 症状：改进不显著、cherry-picked results、缺乏统计测试
- 典型触发语：「The improvements are marginal and may not be statistically significant.」

### 模式 4：评估不全 (Incomplete Evaluation)

- 症状：缺少重要 baselines、资料集太少、没有 ablation
- 典型触发语：「Key baselines such as [X] are missing.」

### 模式 5：方法有缺 (Flawed Methodology)

- 症状：数学错误、不合理的假设、data leakage、不公平比较
- 典型触发语：「There appears to be an error in the derivation of Eq. (X).」

---

## 评分体系速查

### Overall Score (1-10)

| 分数 | 含义 | 建议 |
|------|------|------|
| 10 | 顶级论文，可直接接受 | Strong Accept |
| 8-9 | 优秀论文，明显高于门槛 | Accept |
| 6-7 | 好论文，略高于或在门槛附近 | Weak Accept / Borderline |
| 5 | 在门槛上，有明显的优缺点 | Borderline |
| 3-4 | 低于门槛，有重大问题 | Weak Reject / Reject |
| 1-2 | 明显不合格 | Strong Reject |

### Confidence (1-5)

| 分数 | 含义 |
|------|------|
| 5 | 非常确信——我是这个子领域的专家 |
| 4 | 确信——我熟悉这个领域 |
| 3 | 中等——我了解主要概念但非专家 |
| 2 | 不太确信——部分内容超出我的专业 |
| 1 | 不确信——这不是我的领域 |

完整评分标准请参考 `references/scoring-rubric.md`。

---

## 参考资料与模板

### 参考资料
- `references/review-dimensions.md` — 五大审查维度的完整说明
- `references/scoring-rubric.md` — 完整评分标准
- `references/rejection-patterns.md` — 五大退稿模式的详细说明与范例
- `references/constructive-feedback.md` — 建设性回馈的写法指南

### 模板
- `templates/review-form.md` — 标准审稿表模板
- `templates/meta-review-form.md` — AC meta-review 模板

### 相关技能
- **paper-writing** skill — 论文写作技能，可搭配使用进行修改循环（revision cycle）

---

## 使用方式

### 基本使用

```
请帮我审查这篇论文：[贴上论文内容或提供 PDF 路径]
```

依序执行四个步骤，最终默认产出简体中文正式审稿。

### 指定步骤

```
请只执行 Step 1（批判性审查）
请从 Step 3 开始（我已经有前两步的分析）
```

### 指定会议

```
请以 NeurIPS 2026 的标准审查这篇论文
请以 ACL 2026 的标准审查，特别注意 reproducibility
```

### Meta-review

```
以下是三位 reviewer 的意见，请帮我撰写 meta-review：
[贴上三份 review]
```

使用 `templates/meta-review-form.md` 模板。

---

## 审稿伦理提醒

1. **保密性**：审稿内容不得泄漏给第三方
2. **利益冲突**：如果你认识作者或与论文有利益关系，应主动回避
3. **尊重**：即使论文品质不佳，也应以尊重的态度撰写 review
4. **时效性**：在截止日期前完成审稿是审稿者的责任
5. **一致性**：你的评分应与你的文字评论一致——不要给高分却写满缺点
6. **建设性**：审稿的最终目的是帮助作者改进论文，而非炫耀自己的知识

---

## 常见问题

### Q：如果我不确定某个缺点是否正确怎么办？

写在 Questions for Authors 中，让作者在 rebuttal 中回应。不确定的批评不应作为拒稿的主要理由。

### Q：如何处理 borderline 的论文？

仔细衡量优缺点的相对权重。如果优点明确且重大，而缺点可以在 camera-ready 中修复，倾向接受。如果核心方法有问题，倾向拒稿。

### Q：meta-review 和 individual review 有什么不同？

Meta-review 需要综合所有 reviewer 的意见，找出共识与分歧，并做出最终建议。AC 需要判断哪些 reviewer 的意见更有价值，以及 rebuttal 是否有效回应了主要问题。

### Q：如何与 paper-writing 技能搭配使用？

在完成审稿后，可以将 review 中的建议传递给 **paper-writing** skill，指导作者进行修改。这形成了一个「审稿 -> 修改 -> 再审」的循环。


## 输出语言
默认使用简体中文输出；论文标题、会议名称、方法名、模型名、专有名词、代码和公式保留原文。用户明确要求其他语言时，遵从用户要求。
