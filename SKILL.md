---
name: experiment-modeling-writing
description: >-
  数学建模全流程组合工作流：用 academic-research 设计预实验和论文逻辑，
  用 nature-citation 做不限出版商的文献检索与支撑核验，用 nature-figure
  生成中文且可进入 Adobe Illustrator 修改的科研图，用 ponytail 做代码复用、
  最小化和提交前审查，再用 humanizer-zh 清理中文论文的 AI 腔并保持论证逻辑。
---

# Experiment–Modeling–Writing

这是一个组合入口，不替代下面的子 skill。根据任务读取对应目录中的 `SKILL.md`，必要时组合使用：

1. `academic-research`：预实验设计、baseline/ablation 规划、论文结构和写作逻辑。
2. `nature-citation`：拆分 claim，检索不限来源的文献，保守判断支撑强度并导出引用文件。
3. `nature-figure`：中文科研绘图、证据链设计、SVG/PDF/TIFF 导出和交付前检查。
4. `ponytail`：优先复用现有代码和标准库，删除不必要的抽象，并在提交前审查重复或过度实现。
5. `humanizer-zh`：在论文逻辑确定后清理模板化、宣传腔和机械连接词，保留事实、限定和作者声音。

推荐顺序：问题与假设 → 预实验 → 文献支撑 → 模型与代码 → 图表 → 论文逻辑 → 中文表达审查。

## 使用原则

- 先由 `academic-research` 明确问题、假设、实验和论证链，再进入写作。
- `nature-citation` 默认不限制 Nature、Science 或其他出版商；只有用户明确要求时才收窄期刊范围。
- `nature-figure` 默认将面向读者的图中文字设为中文，并优先保留 SVG/PDF 中的可编辑文字；Adobe Illustrator 的最终微调仍需人工完成。
- `ponytail` 只负责减少无必要的代码和依赖，不删除输入校验、错误处理、安全措施、可复现性检查或用户明确要求的功能。
- `humanizer-zh` 不负责改变结论、补造证据或规避学术审查；它应放在逻辑、引文和数据核验之后。

## 组合调用示例

```text
请使用 experiment-modeling-writing 处理数学建模论文的结果章节：
先用 academic-research 检查实验问题、baseline 和论证逻辑；
再用 nature-citation 为每个科学判断检索不限来源的支撑文献；
用 nature-figure 生成中文、可导出 SVG/PDF 并方便 Illustrator 修改的图；
用 ponytail 检查代码是否重复实现或过度封装；
最后用 humanizer-zh 去除 AI 腔，但不要改变事实、数值、引用和结论强度。
```

详细规则位于各子目录；请不要把题面、原始数据、个人信息或实验产物直接提交到本组合仓库。
