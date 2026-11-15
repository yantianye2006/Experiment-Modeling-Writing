# Academic Research Skills — 调度器

本仓库提供完整的学术研究 Skill 套件，涵盖从论文阅读到撰写、审稿的完整研究流程。

本套件符合 [Agent Skills 开放标准](https://agentskills.io/specification)，同时支援 Claude Code、ChatGPT/Codex CLI、Gemini CLI。

## Skill 路由

| 指令 | Skill | 说明 |
|------|-------|------|
| `/read-paper` | `paper-reading/SKILL.md` | 太奶角色论文导读（简中） |
| `/brainstorm` | `idea-generation/SKILL.md` | 发散→搜索→收敛三阶段构思 |
| `/experiment` | `experiment-design/SKILL.md` | 实验设计与规划 |
| `/prove` | `proof-writer/SKILL.md` | 理论推导与数学证明 |
| `/write-paper` | `paper-writing/SKILL.md` | 论文撰写（顶会标准） |
| `/review` | `paper-review/SKILL.md` | 4步骤学术审稿 |
| `/prof-fit` | `professor-fit-analyser/SKILL.md` | 教授适配度分析 |

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

## 语言惯例

- **预设语言**: 简体中文（分析、解释、讨论）
- **保留原文**: 论文标题、专有名词、数学符号、代码和公式
- **学术词汇**: 参考 `shared/chinese-academic-glossary.md` 确保一致性

## 品质标准

- 每个 `SKILL.md` 必须包含符合 [agentskills.io 标准](https://agentskills.io/specification) 的 YAML frontmatter（name, description 为必填；license, compatibility, metadata 为选填）
- 每个 `SKILL.md` 建议 200–500 行
- Reference 档案提供详细指引，SKILL.md 透过相对路径引用
- 所有模板使用 Markdown 或 LaTeX 格式

## Cross-Reference 规则

- Skill 之间可透过相对路径互相引用：`../paper-writing/SKILL.md`
- 共享资源放在 `shared/` 目录
- 每个 Skill 的 `references/` 仅存放该 Skill 专属的参考资料

## 使用方式

1. 将本仓库 clone 到工作目录
2. 在 Claude Code 中开启该目录
3. 使用上方指令表中的 `/` 指令启动对应 Skill
4. 依照 Skill Pipeline 完成完整研究流程
