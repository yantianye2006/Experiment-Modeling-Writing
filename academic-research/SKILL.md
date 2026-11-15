---
name: academic-research
description: "Complete academic research skill suite covering the full pipeline: paper reading (read/explain papers with storytelling), idea generation (brainstorm research directions), experiment design (plan experiments, ablation, baselines), proof writing (mathematical proofs, LaTeX theorems), paper writing (draft to camera-ready for top venues like NeurIPS/ICLR/ACL), paper review (structured 4-step review with scoring), and professor fit analysis (evaluate advisors, cold emails, interview strategy). Trigger keywords: read paper, brainstorm, experiment design, prove, write paper, review, professor fit, advisor, cold email, LaTeX, research, NeurIPS, ICLR, ACL, arXiv, 读论文, 写论文, 审稿, 实验设计, 数学证明, 研究方向, 教授分析, 选指导教授."
license: MIT
compatibility: Works with Claude Code, ChatGPT/Codex CLI, and Gemini CLI.
metadata:
  author: research-skills
  version: "1.0.0"
---

# Academic Research Skills Suite

## 输出语言

默认使用简体中文输出。论文标题、会议名称、方法名、模型名、专有名词、代码和公式保留原文；用户明确要求其他语言时，遵从用户要求。

一套完整的学术研究 Skill 套件，涵盖从论文阅读到撰写、审稿的完整研究流程。支援 Claude Code、ChatGPT/Codex CLI、Gemini CLI。

---

## Skill 路由表

根据使用者的意图，载入对应的子 Skill：

| 触发条件 | 子 Skill | 路径 | 说明 |
|----------|---------|------|------|
| 读论文、解释论文、paper reading、看不懂这篇 | Paper Reading | [paper-reading/SKILL.md](paper-reading/SKILL.md) | 太奶角色论文导读（简中） |
| 想 idea、brainstorm、研究方向、下一步做什么 | Idea Generation | [idea-generation/SKILL.md](idea-generation/SKILL.md) | 发散→搜索→收敛三阶段构思 |
| 实验设计、ablation、baseline、跑什么实验 | Experiment Design | [experiment-design/SKILL.md](experiment-design/SKILL.md) | 实验设计与规划 |
| 数学证明、prove、theorem、推导 | Proof Writer | [proof-writer/SKILL.md](proof-writer/SKILL.md) | 理论推导与数学证明 |
| 写论文、paper writing、improve my paper、LaTeX | Paper Writing | [paper-writing/SKILL.md](paper-writing/SKILL.md) | 论文撰写（顶会标准） |
| review、审稿、reviewer 会怎么说、这篇能上吗 | Paper Review | [paper-review/SKILL.md](paper-review/SKILL.md) | 4 步骤学术审稿 |
| 教授分析、professor fit、选指导教授、cold email、申请策略 | Professor Fit Analyser | [professor-fit-analyser/SKILL.md](professor-fit-analyser/SKILL.md) | 教授适配度分析与申请策略 |

**指引**：当使用者的请求匹配上方触发条件时，请读取对应路径的 `SKILL.md` 并依照其指示执行。如果使用者的需求横跨多个 Skill，请依照下方 Pipeline 顺序依序处理。

---

## Skill Pipeline

```
professor-fit-analyser ─┐
                        ↓
paper-reading ──→ idea-generation ──→ experiment-design
      │                                       │
      ↓                                       ↓
paper-review ←── paper-writing ←──── proof-writer
      │                 ↑
      └─────────────────┘  (revision cycle)
```

---

## 语言惯例

- **预设语言**: 简体中文（分析、解释、讨论）
- **保留原文**: 论文标题、专有名词、数学符号、代码和公式
- **学术词汇**: 参考 [shared/chinese-academic-glossary.md](shared/chinese-academic-glossary.md) 确保一致性

---

## 共享资源

- [shared/chinese-academic-glossary.md](shared/chinese-academic-glossary.md) — 中英学术词汇对照
- [shared/conference-standards.md](shared/conference-standards.md) — 各顶会格式标准
- [shared/researcher-philosophies.md](shared/researcher-philosophies.md) — 研究者哲学与写作风格

---

## 跨平台安装

本套件符合 [Agent Skills 开放标准](https://agentskills.io/specification)，可在以下平台使用：

### Claude Code
```bash
# 方法一：Clone 到 skills 目录
git clone <repo-url> ~/.claude/skills/academic-research

# 方法二：在专案中使用
git clone <repo-url> .claude/skills/academic-research
```

### ChatGPT / Codex CLI
```bash
git clone <repo-url> ~/.codex/skills/academic-research
# 或在专案中
git clone <repo-url> .codex/skills/academic-research
```

### Gemini CLI
```bash
git clone <repo-url> ~/.gemini/skills/academic-research
# 或在专案中
git clone <repo-url> .gemini/skills/academic-research
```

### 通用方式
将本仓库目录复制到你的 AI agent 的 skills 目录即可。根目录 `SKILL.md` 作为入口，agent 会透过 `*/SKILL.md` 模式自动发现所有子 skills。
