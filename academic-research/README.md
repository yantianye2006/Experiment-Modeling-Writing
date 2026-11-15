# Academic Research Skills

一套完整的学术研究 Skill 套件，符合 [Agent Skills 开放标准](https://agentskills.io/specification)。支援 **Claude Code**、**ChatGPT / Codex CLI**、**Gemini CLI**。

## Usage  
Claude Code: `git clone <repo> ~/.claude/skills/academic-research` 

ChatGPT/Codex CLI: `git clone <repo> ~/.codex/skills/academic-research` 

Gemini CLI: `git clone <repo> ~/.gemini/skills/academic-research` 

## 功能总览

| # | Skill | 说明 |
|---|-------|------|
| 01 | Paper Reading | 太奶角色论文导读，简中叙事风格 |
| 02 | Idea Generation | 发散→搜索→收敛三阶段构思 |
| 03 | Experiment Design | 假设→变数→指标→Baseline→Ablation |
| 04 | Proof Writer | 理论推导与 LaTeX 数学证明 |
| 05 | Paper Writing | 顶会标准论文撰写 |
| 06 | Paper Review | 4步骤学术审稿流程 |
| 07 | Professor Fit Analyser | 教授适配度分析与申请策略 |

## 研究流程 Pipeline

```
教授分析 ─┐
   07     ↓
阅读论文 → 发想 Idea → 设计实验 → 理论推导 → 撰写论文 → 审稿修改
   01          02          03          04          05         06
                                                    ↑          │
                                                    └──────────┘
                                                   (revision cycle)
```

## 安装与使用

本套件支援三大 AI agent 平台。选择你使用的平台，将仓库 clone 到对应的 skills 目录即可。

### Claude Code

```bash
# 使用者层级（全域可用）
git clone <repo-url> ~/.claude/skills/academic-research

# 专案层级（仅该专案可用）
git clone <repo-url> .claude/skills/academic-research
```

在 Claude Code 中使用 `/` 指令：

```
/read-paper          # 开始导读一篇论文
/brainstorm          # 从论文出发发想新 Idea
/experiment          # 设计实验方案
/prove               # 撰写数学证明
/write-paper         # 撰写论文各章节
/review              # 审稿一篇论文
/prof-fit            # 分析教授适配度
```

### ChatGPT / Codex CLI

```bash
# 使用者层级
git clone <repo-url> ~/.codex/skills/academic-research

# 专案层级
git clone <repo-url> .codex/skills/academic-research
```

Skills 会自动被侦测。可透过 `@academic-research` 提及来启用，或让 agent 根据任务自动匹配。

### Gemini CLI

```bash
# 使用者层级
git clone <repo-url> ~/.gemini/skills/academic-research

# 专案层级
git clone <repo-url> .gemini/skills/academic-research
```

Skills 会透过 `activate_skill` 机制自动匹配使用者意图。

### 通用方式

将本仓库目录复制到你的 AI agent 的 skills 目录即可。根目录 `SKILL.md` 作为入口，agent 会透过 `*/SKILL.md` 模式自动发现所有子 skills。

## 目录结构

```
├── SKILL.md                     # 根入口（monorepo skill，路由到子 skills）
├── CLAUDE.md                    # Claude Code 调度器（定义 / 指令路由）
├── paper-reading/               # 论文导读
│   ├── SKILL.md
│   └── references/
├── idea-generation/             # Idea 发想
│   ├── SKILL.md
│   └── references/
├── experiment-design/           # 实验设计
│   ├── SKILL.md
│   ├── references/
│   └── templates/
├── proof-writer/                # 理论证明
│   ├── SKILL.md
│   └── references/
├── paper-writing/               # 论文撰写
│   ├── SKILL.md
│   └── references/
├── paper-review/                # 学术审稿
│   ├── SKILL.md
│   ├── references/
│   └── templates/
├── professor-fit-analyser/      # 教授适配度分析
│   ├── SKILL.md
│   ├── references/
│   └── templates/
└── shared/                      # 共享资源
    ├── chinese-academic-glossary.md
    ├── conference-standards.md
    └── researcher-philosophies.md
```

## 语言说明

- 分析、解释、讨论：简体中文
- LaTeX 说明、正式审稿：默认简体中文；论文正文、代码和公式按用户要求或保留原文
- 数学符号与定理：英文

## 设计参考

- [Agent Skills 开放标准](https://agentskills.io/specification)
- [Orchestra-Research/AI-Research-SKILLs](https://github.com/Orchestra-Research/AI-Research-SKILLs)
- [Master-cai/Research-Paper-Writing-Skills](https://github.com/Master-cai/Research-Paper-Writing-Skills)

## License

MIT
