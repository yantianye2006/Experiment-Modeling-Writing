# Experiment-Modeling-Writing

数学建模全流程的组合 skills：从预实验和文献调研，到代码、科研图和论文成稿。

这个仓库不是把几个提示词简单堆在一起，而是把它们放进数学建模实际会经历的顺序中：先弄清楚问题和证据，再做实验和实现，最后处理图表与文字。

## 我如何在数学建模中使用它们

### 1. academic-research：先把实验和论证链想清楚

我用 `academic-research` 的 `experiment-design` 规划预实验、baseline、ablation、评估指标和验证方式；用 `paper-writing` 检查论文的主线、章节功能、论点顺序和结果解释。

在建模项目中，它主要回答：

- 这个问题真正要验证的假设是什么？
- 预实验能否区分不同模型路线？
- baseline 和 ablation 是否足以支撑结论？
- 每张表、每个实验和每个小结在论证链中承担什么作用？

它应当先于大规模调参和论文润色使用。实验没有定义清楚时，写作再漂亮也只是把不确定性藏起来。

### 2. nature-citation：文献不限来源，但支撑必须匹配

我对 `nature-citation` 做的使用约定是：默认检索范围为所有可靠来源，不把文献搜索限制在 Nature 旗下期刊。只有在投稿目标或用户明确指定时，才切换到 Nature、Science、Cell、CNS 或其他期刊范围。

它用于：

- 把论文段落拆成可核验的科学 claim；
- 检索背景、方法、机制和对比结论的支撑文献；
- 区分“标题相关”与“摘要或正文真正支持”；
- 保守标记 support 强度，避免把相关性写成因果性；
- 导出 RIS、ENW 或 Zotero RDF，方便后续管理。

它和 `academic-research` 的关系是：前者负责文献证据与引用，后者负责研究问题、实验和论文结构。

### 3. nature-figure：中文科研图，并为 Illustrator 留出空间

我使用 `nature-figure` 生成投稿级科研图和多面板图，重点做三件事：

1. 先写清楚图要回答的科学问题和证据链；
2. 默认把图题、坐标轴、图例、注释和面板标题写成中文；
3. 优先输出可编辑的 SVG/PDF，同时保留适合投稿的 TIFF/PNG 等格式。

这样生成的图可以先由 Python 或 R 完成数据映射和布局，再交给 Adobe Illustrator 做字体、间距、箭头、标注和版面微调。Illustrator 的修改不能替代数据核验，最终仍要回看导出文件和实际尺寸。

### 4. ponytail：代码复用、删掉重复实现，再提交

我使用 `ponytail` 作为代码阶段的“最小实现门禁”：

- 先查项目里是否已经有可复用的函数、工具或数据结构；
- 标准库和原生平台能解决时，不额外引入依赖；
- 删除只为“以后可能有用”而写的抽象层；
- 检查同一逻辑是否在多个脚本中重复实现；
- 提交前做一次 diff、调用链和最小测试审查。

它不是让代码变短就算成功。输入校验、错误处理、数据安全、可复现性和必要测试不能为了少写几行而删掉。

### 5. academic-research + humanizer-zh：先保逻辑，再去 AI 腔

这两个 skill 不能颠倒顺序。

先用 `academic-research` 确认论文的研究问题、证据链、章节逻辑和结论边界；再用 `humanizer-zh` 清理中文中的模板化表达、空泛拔高、机械连接词、过度排比和宣传腔。

`humanizer-zh` 的使用边界是：

- 保留数字、条件、否定、时间、引用、归因和不确定程度；
- 不把相关关系改成因果关系；
- 不添加原文没有的数据、人物、结论或文献；
- 不为了“像真人”而把正式学术语气改成随意聊天。

它的目标是让论证更清楚、句子更自然，而不是规避 AI 检测器。

## 推荐工作流

```text
数学问题与假设
        ↓
academic-research
预实验、baseline、ablation、论证链
        ↓
nature-citation
文献调研、claim 支撑、引用导出
        ↓
ponytail
代码复用、删重、最小实现、提交前检查
        ↓
nature-figure
中文图表、证据链、多面板布局、可编辑导出
        ↓
academic-research
结果章节与全文逻辑
        ↓
humanizer-zh
中文表达去模板化、去 AI 腔、保留学术边界
```

## 目录

```text
Experiment-Modeling-Writing/
├── SKILL.md                    # 组合入口
├── academic-research/          # 学术研究全套子 skills
├── nature-citation/            # 文献检索、核验和引用导出
├── nature-figure/              # 中文投稿级科研绘图
├── ponytail/                   # 代码最小化与复用审查
├── humanizer-zh/               # 中文文本人性化编辑
└── THIRD_PARTY_NOTICES.md      # 上游项目、许可证和致谢
```

## 安装与使用

直接克隆：

```bash
git clone https://github.com/yantianye2006/Experiment-Modeling-Writing.git
```

如果使用 Codex，可将需要的子目录复制到 skills 目录；也可以把仓库根目录作为组合 skill 使用。入口文件为根目录的 `SKILL.md`。

在对话中可以这样调用：

```text
使用 experiment-modeling-writing 帮我检查这次数学建模实验：先设计预实验和 baseline，再找支撑文献，最后给出代码、图表和论文结果章节的交接清单。
```

## 重要说明

- 这些 skill 是工作流和编辑规范，不会替代研究者对题意、数据、模型和结果的判断。
- 文献搜索结果必须回到摘要、正文或出版商页面核验，不能因为标题相似就引用。
- 科研图通过自动检查后仍需人工看最终尺寸、字体、碰撞和信息层级。
- `humanizer-zh` 不是 AI 检测器，也不保证通过任何检测工具。
- 原始题面、原始数据、实验结果、个人路径和密钥不要上传到这个仓库。

## 上游项目与致谢

本组合仓库感谢以下开源项目及其作者。各子目录保留对应 skill 的实际版本；使用、修改和再发布时请同时遵守上游许可证。

| 组合目录 | 上游项目 | 主要用途 |
| --- | --- | --- |
| `academic-research` | [voidful/academic-skills](https://github.com/voidful/academic-skills) | 学术研究、实验设计、论文写作和审稿流程 |
| `nature-citation`、`nature-figure` | [Yuan1z0825/nature-skills](https://github.com/Yuan1z0825/nature-skills) | 文献引用核验与投稿级科研绘图 |
| `ponytail` | [DietrichGebert/ponytail](https://github.com/DietrichGebert/ponytail) | 最小实现、代码复用和过度工程审查 |
| `humanizer-zh` | [blader/humanizer](https://github.com/blader/humanizer)、[hardikpandya/stop-slop](https://github.com/hardikpandya/stop-slop) | 英文规则基线与实用去套话检查；中文适配可参考 [Show-Chan97/Humanizer-zh](https://github.com/Show-Chan97/Humanizer-zh) |

感谢这些项目把可复用的研究、编程和写作经验整理成了 agent 可以调用的 skill。这个仓库的工作只是把它们放进数学建模的实际流程中，并按我的使用场景补充组合说明；不主张拥有上游作品的作者权利。

## License

各子目录的许可证和上游项目不同，请以对应目录中的许可证和 `THIRD_PARTY_NOTICES.md` 为准。组合入口、工作流说明和本 README 采用 MIT License，见仓库根目录 `LICENSE`。
