# 进阶写作技巧

## 如何回应 "incremental" 的质疑

当 reviewer 说工作 incremental 时，通常意味著：

1. **差异化不够清楚**：在 Introduction 中加入 "Unlike [prior work] which ..., our approach fundamentally differs in ..."
2. **结果提升不够大**：考虑加入更多困难场景的实验，或更深入的分析。
3. **insight 不够深**：增加 "Why does it work?" 的分析段落。

## 如何处理 "limited novelty" 的质疑

1. 强调 **insight** 而非 **technique**。
2. 展示方法揭示的**新发现**。
3. 证明看似简单的方法背后有**深刻的理解**。

## 如何处理 "insufficient experiments" 的质疑

1. 加入更多 **dataset**（至少 3 个）。
2. 加入更多 **baseline**（至少 5 个）。
3. 加入 **ablation study** 验证每个组件。
4. 加入 **qualitative analysis** 展示成功和失败案例。
5. 加入 **efficiency comparison**（FLOPs、参数量、推理时间）。

## 如何提升 Clarity 分数

1. 让非本领域的人阅读，看他们能否理解。
2. 每个 section 开头加一句 roadmap。
3. 使用 consistent notation。
4. 多用 "Specifically, ..." "In particular, ..." "More concretely, ..." 引导读者。
5. 避免跳跃式的逻辑，确保每一步都有铺陈。
