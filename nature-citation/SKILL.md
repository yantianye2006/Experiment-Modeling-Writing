---
name: nature-citation
description: >-
  为论文段落或科学判断检索并核验学术引用：拆分可引用 claim，保守评估不同强度的
  support，生成文本—文献对应关系，并导出 RIS、ENW 或 Zotero RDF。默认检索不限出版商
  或期刊品牌，以 claim 匹配度和证据质量优先；用户明确要求时可限定 Nature Portfolio、
  Science family、Cell Press、CNS 或旗舰刊。用于分段引用、补引用、找支撑文献、写论文加
  参考文献、构建 reference list，以及 EndNote/RIS/ENW/Zotero RDF 导出。默认以简体中文
  输出说明和报告，文献题名、作者、期刊、DOI 与标准术语保留原文。
metadata:
  author: Yuan1z skill, refactored into static/dynamic layers
---

# Nature Citation — 学术引用路由

This skill is split into two layers:

- A **static layer** under `static/` that holds versioned, reusable content fragments (core principles and scope, the Chinese-user operating mode, and the citation workflow).
- A **dynamic layer** (this file plus `manifest.yaml`) that loads the core every time and reaches for heavier material only when a step needs it.

Do not try to apply the citation logic from memory or from this router. Always load fragments from disk as described below.

## Routing protocol

Follow these four steps every time the skill is invoked.

### 1. Load the manifest and the core layer

Read [manifest.yaml](manifest.yaml). Then read every file listed under `always_load`:

- `static/core/principles.md` — what the skill produces, the default broad scholarly scope, optional journal restrictions, source hierarchy, and search-quality rules.
- `static/core/chinese-mode.md` — default Chinese output and language handling for manuscript text and search queries.
- `static/core/workflow.md` — the seven-step workflow and the final report format.

### 2. No content axis — confirm scope and language inline

Unlike the other nature-* skills, nature-citation has no fragment axis. Its variation is runtime parameters, not different content bodies:

- **source scope** — default to `all`, with no publisher-family or journal-brand filter. Use `nature`, `science`, `cell`, `cns`, or `flagship` only when the user explicitly requests that restriction; pass it to the script as `--scope`.
- **output language** — default to Simplified Chinese unless the user asks for another language. Keep titles, authors, journals, DOI, standard abbreviations, and precision-critical terms in their source language. Scientific search queries may remain in English.
- **input length** — if there are more than ~10 segments, switch to the batched long-article strategy in `references/script-usage.md`.

State the detected scope and date limits in one short Chinese line before searching.

### 3. Run the workflow

Follow the seven steps in `core/workflow.md`: segment, parse, search, evaluate support conservatively, validate complete structured author metadata, export one reference-manager file, generate review artifacts when useful, and report with the HTML browser path first. Prefer `scripts/nature_citation.py` for the search/export when internet access is available; open `references/script-usage.md` for its full flag list and the long-article batch strategy. When DOI metadata lacks given names, refetch the record by PMID or verify it against the publisher rather than exporting surname-only `AU` fields.

Never present a paper as support merely because its title is related, and never cite a metadata-only candidate without checking the abstract or publisher page. Do not invent missing bibliographic fields.

### 4. Reach for references only when needed

The files under `references/` are deep references, not defaults. Open them on demand per the `references.on_demand` table in the manifest:

- running the script, full flags, long-article batching → `references/script-usage.md`.
- turning a claim into search queries and support grades → `references/search-strategy.md`.
- an explicitly requested Nature/CNS journal-family boundary → `references/journal-scope.md`.
- RIS / EndNote / Zotero RDF export details → `references/ris-endnote.md`.

## Why this split

- The static layer is versioned and reviewable; the core stays small for a normal short run.
- The dynamic layer keeps each invocation cheap: the script flag dump and long-article strategy load only when actually running a search.
- The router itself is short on purpose. Update fragments and references, not this file, when adding scope.
- This structure mirrors `nature-writing`, `nature-polishing`, `nature-reader`, `nature-paper2ppt`, and `nature-figure`.
