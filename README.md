# Experiment-Modeling-Writing

一套面向数学建模全流程的组合 skills：覆盖从预实验、文献调研，到代码整理、科研绘图与论文成稿的各个环节。

这个仓库并不是把几个提示词简单堆在一起，而是按照数学建模实际推进的顺序把它们串起来：先理清问题和证据，再动手写代码和做实验，最后打磨图表与文字。

> 在实际比赛中，作者是配合自研的上下文管理 skill —— [modeling-context](https://github.com/yantianye2006/modeling-context) 一起使用的，用它来统一维护赛题理解、阶段门禁与决策记录，再由本套工作流承接具体的实验、科研绘图与写作任务。

## 使用说明（必读）

在开始之前，有几点真实的使用体验和前提想先说明：

1. **它们不是“全自动数模智能体”，而是辅助工具**
   这套 skills 更多是**工具性质**，需要你自己主动和 Agent 对话、分阶段调用，而不是扔进去一个题面就坐等论文出炉。
   - **好处**：工作流非常动态、个性化，下文分享的顺序只是作者自己的实战经验，你可以根据赛题节奏随时自助调整；
   - **坏处**：上手门槛偏高，**没有那么“轮椅”**。（这种“人脑高于电脑、自己把握节奏与细节”的取向，其实也受到了 [modeling-context](https://github.com/yantianye2006/modeling-context) 中分享的建模哲学影响。）
2. **测试环境有限**
   本套工作流目前只在 **Codex** 上与 GPT 老师配合使用和测试过，其他 Agent harness（如 Claude Code、Cursor、Gemini CLI 等）的适配情况尚未经过测试。
3. **实战效果：只是合格，远非完美，仍需人工把关**
   部分 skill 在 Codex 上的表现目前还没有达到“惊艳”的程度，作者用这套工作流最终也只是拿了**国二**。具体踩坑体验如下：
   - **`nature-figure` 绘图**：数据可视化图往往需要和 Codex 进行**多轮迭代**并给出足够细致的引导，才能画出比较像样的效果；导出后**建议配合 Adobe Illustrator 精修**。另外，用它直接生成的流程图通常比较平淡。
   - **`humanizer-zh` + `academic-research` 写作**：这套组合用来应付知网等 AI 检测器其实很 easy，但成文读起来很多地方还是“一眼 GPT”（比如 GPT 特别爱用的“不是……而是……”句式非常明显）。**强烈建议最后人工微调关键句子**，才能真正去掉机器味。

---

## 作者如何在数学建模中使用它们

### 1. `academic-research`：先把实验和论证链想清楚

作者主要用 `academic-research` 中的 `experiment-design` 规划预实验、baseline、ablation、评估指标和验证方式；用 `paper-writing` 检查论文主线、章节功能、论点顺序与结果解释。

在建模项目中，它主要帮我回答四个问题：

- 这个问题真正要验证的假设是什么？
- 预实验能不能有效区分不同的模型路线？
- baseline基线设计和消融实验是否足以支撑后续结论？
- 每张表、每个实验、每个小结在整个论证链里各自承担什么作用？

这部分被我用来进行正式建模前的预实验设计。

### 2. `nature-citation`：文献不限来源，但支撑必须匹配

作者对 `nature-citation` 做了一点微调：默认检索范围为所有可靠学术来源，不把文献搜索局限于 Nature 旗下期刊，放开了引用限制。
它主要用来：

- 在建模预实验以及思维碰撞的时候调研文献；
- 保守标注支撑强度，为建模的决策提供支持强度；
- 导出 RIS、ENW 或 Zotero RDF，方便导入文献管理工具核查。

它和 `academic-research` 的分工很明确：前者管文献证据与引用，后者管研究问题、实验设计与论文结构。

### 3. `nature-figure`：中文科研图，并为 Illustrator 留出精修空间

用 `nature-figure` 生成科研图和多面板组合图。作者微调了原始skill，将输出语言改为中文，同时优先导出选项为pdf和svg，便于后续Adobe Illustrator修改。该skill的优势：

1. 先想清楚这张图要回答什么问题、承担哪一环证据，从而选择合适的可视化图表；
2. 把于宏观的面板排布、子图内容、配色方案等调整交给Agent做，细微的调整则交由人完成



### 4. `ponytail`：代码复用、删掉冗余，再提交

我把 `ponytail` 当作代码阶段的“最小实现门禁”来用：

- 先查项目里是否已经有可复用的函数、工具或数据结构；
- 标准库和现有工具能搞定的时候，不额外引入新依赖；
- 删掉那些只为“以后可能用得上”而写的过度抽象层；
- 排查同一段逻辑是不是在多个脚本里复制粘贴了；
- 提交前过一遍 diff、调用链和最小测试。

今年很多选手提交的论文页数膨胀到了200页，其中膨胀最厉害的就是代码部分。事实上，很多代码根本没有必要放进附录，一些代码中也充斥GPT老师高度防御的编程习惯。作者除了在编程中使用，在最后提交的时候还用这个skill去除没有必要的防御性设计以及将问题零散的代码合并成一个完整的运行程序。

### 5. `academic-research` + `humanizer-zh`：先保逻辑，再去 AI 腔

用 `academic-research` 把研究问题、证据链、章节逻辑和结论边界定死；再用 `humanizer-zh` 清理中文里常见的模板化表达、空泛拔高、机械连接词、过度排比和腔调问题。

这两个skill联合使用有这些优点：

- 保留原文的数字、条件、否定词、时间、引用和不确定程度；
- 不把相关关系擅自改成因果关系；
- 不脑补原文没有的数据、结论或文献；
- 不为了“像人话”而把正式学术语体改得过于口语化。

它的核心目标是让论证更顺畅、句子更自然。对于知网、万方、维普三个AIGC检测器，数模论文超过15%算炸单，但正如开头所说，遇到“不是……而是……”这类典型 GPT 句式时，还是需要自己上手改一改。

---

## 推荐工作流（仅供参考，可自行调整）

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
中文图表、证据链、多面板布局、可编辑导出（建议配合 AI 精修）
        ↓
academic-research
结果章节与全文逻辑串联
        ↓
humanizer-zh + 人工微调
中文表达去模板化、去 AI 腔、保留学术边界
```

---

## 目录结构

```text
Experiment-Modeling-Writing/
├── SKILL.md                    # 组合入口
├── academic-research/          # 学术研究全套子 skills
├── nature-citation/            # 文献检索、核验和引用导出
├── nature-figure/              # 中文科研绘图
├── ponytail/                   # 代码最小化与复用审查
├── humanizer-zh/               # 中文文本人性化编辑
└── THIRD_PARTY_NOTICES.md      # 上游项目、许可证和致谢
```

---

## 安装与调用

直接克隆仓库：

```bash
git clone https://github.com/yantianye2006/Experiment-Modeling-Writing.git
```

在 Codex 中使用时，既可以把需要的子目录分别放进你的 `skills` 目录，也可以直接把仓库根目录作为一个组合 skill 使用（入口文件为根目录的 [SKILL.md](./SKILL.md)）。

在对话中可以这样触发：

```text
使用 experiment-modeling-writing 帮我推进这次数学建模实验：先一起梳理预实验和 baseline 设计，再检索支撑文献，最后整理出代码、图表和论文结果章节的交接清单。
```

---

## 实践小贴士

- 文献检索到的结果一定要回看摘要或原文核验，今年一篇“优秀论文”被查出参考文献DOI号是编造的。
- 科研图跑完脚本后务必人工检查最终尺寸、字号、元素遮挡和信息层级。

---

## 致谢

感谢各位来自不同领域的大佬愿意分享自己在 AI 协作科研中的发现和经验，我得以站在巨人的肩膀上，调整出自己的数模比赛工作流。

本组合仓库基于以下优秀开源项目整理与适配（各子目录的完整许可证与版权信息见 [THIRD_PARTY_NOTICES.md](./THIRD_PARTY_NOTICES.md)）：

| 组合目录 | 上游项目 | 主要用途 |
| --- | --- | --- |
| `academic-research` | [voidful/academic-skills](https://github.com/voidful/academic-skills) | 学术研究、实验设计、论文写作和审稿流程 |
| `nature-citation`、`nature-figure` | [Yuan1z0825/nature-skills](https://github.com/Yuan1z0825/nature-skills) | 文献引用核验与科研绘图 |
| `ponytail` | [DietrichGebert/ponytail](https://github.com/DietrichGebert/ponytail) | 最小实现、代码复用和过度工程审查 |
| `humanizer-zh` | [blader/humanizer](https://github.com/blader/humanizer)、[hardikpandya/stop-slop](https://github.com/hardikpandya/stop-slop) | 英文规则与去套话检查；中文适配参考 [Show-Chan97/Humanizer-zh](https://github.com/Show-Chan97/Humanizer-zh) |

---

## License

各子目录遵循对应上游项目的开源协议（详见各自目录及 [THIRD_PARTY_NOTICES.md](./THIRD_PARTY_NOTICES.md)）；本仓库的组合入口、工作流说明与文档采用 MIT License，见根目录 [LICENSE](./LICENSE)。
