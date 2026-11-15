# Conclusion 结论写作指南

## 核心原则

结论是读者（和 reviewer）阅读的最后一个部分。它的功能不是重复前文，而是提炼出最核心的 takeaway，并诚实地讨论限制和展望。好的结论让 reviewer 带著正面印象结束阅读；坏的结论让人觉得虎头蛇尾。

---

## 三段式结构

### 第 1 段：总结贡献（Summary）

用 3-5 句话回顾论文的核心内容。注意：是**提炼重点**，不是**逐章复述**。

```latex
\section{Conclusion}
\label{sec:conclusion}

We presented SparseRecon, a coarse-to-fine framework for
high-quality 3D reconstruction from sparse input views.
Our key insight is that an explicit, even coarse, geometric
proxy provides strong structural guidance that enables
neural implicit representations to produce coherent results
in unobserved regions. Through a geometry-conditioned
refinement module, our method adaptively focuses
representational capacity on geometrically complex areas.
Experiments on three benchmarks demonstrate consistent
improvements over existing methods, with an average gain
of 2.3~dB PSNR using only 3 input views.
```

**要点**：
- 第一句重述方法名称和核心任务
- 第二句回顾核心 insight（不是技术细节）
- 最后一句用数字总结最重要的结果
- 不要引入任何新资讯

### 第 2 段：Limitations（限制）

**为什么要写 Limitations？**

1. **诚实性**：reviewer 会更尊重诚实面对限制的作者
2. **预防质疑**：主动承认限制比被 reviewer 指出要好得多
3. **顶会要求**：NeurIPS 2021 起明确要求 broader impact 和 limitations

```latex
\paragraph{Limitations.}
Our method has several limitations.
First, the cost-volume-based geometry estimation assumes
approximate Lambertian reflectance, leading to degraded
performance on highly specular surfaces such as glass and
metal (\cref{fig:failure}a).
Second, our depth sampling strategy uses a fixed number
of hypotheses ($D = 128$), which may be insufficient for
scenes with large depth ranges.
Third, while our method is significantly faster than
per-scene optimization approaches, the stereo network
adds approximately 30\% overhead compared to direct
neural rendering methods.
```

**注意事项**：
- 限制必须是**真实的、具体的**
- 不要故意写「假限制」来显示你有想过
- 不要写你已经解决的问题（"A limitation is X, but we address it by..."）
- 每个限制最好附带一个可能的解决方向

### 第 3 段：Future Work（未来工作）

**好的 future work** 从 limitations 自然延伸出来：

```latex
\paragraph{Future Work.}
Several promising directions emerge from this work.
Integrating material-aware rendering~\cite{ref} could
address the specular surface limitation.
Adaptive depth sampling strategies~\cite{ref2} may
improve efficiency and quality for scenes with varying
depth complexity.
Beyond reconstruction, our coarse-to-fine geometric
reasoning framework may benefit other sparse-view tasks
such as semantic segmentation and object detection,
which we plan to explore in future work.
```

**注意事项**：
- 要具体，不要写 "We will improve our method in the future"
- 每个方向最好引用一篇相关论文，表示可行性
- 2-3 个方向即可，不要列太多
- 至少有一个方向超越当前问题，展示更广泛的影响

---

## 不要引入新资讯

结论中最常见的错误是引入前文没有的新资讯：

```latex
% ❌ 引入了新的实验结果
In conclusion, our method also works well on
indoor scenes (achieving 28.1 dB on ScanNet).

% ❌ 引入了新的方法细节
We note that adding a discriminator loss further
improves the visual quality.

% ❌ 引入了新的 claim
Our framework can be easily extended to video
reconstruction, achieving real-time performance.

% ✅ 只总结前文已有的内容
Our experiments demonstrate consistent improvements
across three benchmarks, validating the effectiveness
of explicit geometric guidance for sparse-view
reconstruction.
```

**黄金法则**：结论中的每一句话都应该能在前文找到对应的内容。

---

## 长度建议

| 会议 | 结论建议长度 | 备注 |
|------|-----------|------|
| NeurIPS/ICML/ICLR | 0.3-0.5 页 | 简洁为上 |
| CVPR/ECCV | 0.3-0.5 页 | 可以稍短 |
| ACL/EMNLP | 0.3-0.5 页 | 通常包含 ethical considerations |
| AAAI | 0.25-0.3 页 | 版面紧张，尽量精简 |

**通用建议**：结论不应超过半页。如果你写了超过半页，几乎一定包含了不必要的重复或新资讯。

---

## Broader Impact（社会影响）

部分会议（如 NeurIPS）要求或鼓励讨论 broader impact：

```latex
\paragraph{Broader Impact.}
Our work on sparse-view 3D reconstruction has potential
applications in reducing the data acquisition cost for
3D content creation, making 3D capture more accessible.
However, improved reconstruction technology could also
be misused for unauthorized 3D scanning of private
spaces or for creating deepfake 3D content. We encourage
the community to develop appropriate safeguards alongside
technical advances.
```

**位置**：通常放在 Conclusion 最后，或作为独立的 section。

---

## 完整范例

```latex
\section{Conclusion}
\label{sec:conclusion}

We presented SparseRecon, a coarse-to-fine framework for
3D reconstruction from sparse input views. By introducing
an explicit geometry proxy as structural guidance, our
method overcomes the ill-posed nature of sparse-view
reconstruction, producing coherent and detailed results
in both observed and unobserved regions. Extensive
experiments on DTU, BlendedMVS, and Tanks\&Temples
demonstrate that SparseRecon consistently outperforms
existing methods, achieving an average improvement of
2.3~dB PSNR while using only 3 input views.

\paragraph{Limitations.}
Our method assumes approximately Lambertian surfaces and
may produce artifacts on highly specular objects. The
fixed depth sampling resolution ($D = 128$) can be
suboptimal for scenes with extreme depth variation.
Additionally, our approach requires known camera poses,
limiting its applicability in fully uncalibrated settings.

\paragraph{Future Work.}
Promising extensions include integrating material-aware
rendering to handle non-Lambertian surfaces, adopting
adaptive depth sampling for improved efficiency, and
jointly estimating camera poses to remove the calibration
requirement. We also plan to explore the application of
our geometric reasoning framework to downstream tasks
such as sparse-view semantic understanding.
```

---

## 自我检查清单

```
□ 是否用 3-5 句话总结了核心贡献？
□ 是否提到了最重要的数字结果？
□ 是否列出了 2-3 个真实的 limitations？
□ Limitations 是否具体而非笼统？
□ 是否列出了 2-3 个 future work 方向？
□ Future work 是否从 limitations 自然延伸？
□ 是否没有引入新资讯？
□ 总长度是否控制在半页以内？
□ 是否需要 broader impact 段落？
```

---

*回到主文件 → `../SKILL.md`*
