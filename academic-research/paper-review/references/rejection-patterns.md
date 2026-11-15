# 五大退稿模式：详细说明与范例

本文件详细说明学术论文审稿中最常见的五大退稿模式，包含常见症状、范例情境以及如何在审稿中恰当地指出这些问题。

---

## 模式 1：贡献不足 (Insufficient Contribution)

### 定义

论文所提出的想法或方法缺乏足够的新颖性或贡献度，不足以构成一篇独立的学术论文。

### 常见症状

1. **增量改进**：只是在已有方法上做了微小的修改（如换一个 loss function、加一个 layer）
2. **Trivial 延伸**：将 A 方法直接搬到 B 问题上，没有新的技术挑战
3. **已知结果的简单组合**：将两个已有方法拼在一起，没有新的洞见
4. **工程改进而非研究贡献**：主要是调参或 tricks 的堆叠
5. **与 concurrent work 高度重叠**：独立发展但贡献被抢先

### 范例情境

**情境 A：增量改进**
> 一篇论文声称提出了「新的」注意力机制，但仔细一看只是把 dot-product attention 改成 cosine similarity attention，没有理论解释也没有显著的实验改进。

**情境 B：简单搬移**
> 一篇论文把 NLP 中已经很成熟的 pre-training + fine-tuning 范式搬到一个新的小领域，方法完全一样，只是换了资料集，且没有遇到任何新的技术挑战。

**情境 C：结果组合**
> 一篇论文同时使用 data augmentation + knowledge distillation + label smoothing，每个技术都是已知的，组合也是直觉上显然的，且没有分析为什么这个组合特别有效。

### 如何在审稿中指出

**推荐的表述方式：**

- 「The contribution appears to be incremental over [prior work X]. The key differences are [A, B], but these modifications seem straightforward and do not present significant technical challenges.」
- 「While the application domain is new, the methodology closely follows [X] without addressing domain-specific challenges. It would strengthen the paper to identify and tackle unique challenges in this setting.」
- 「The paper combines several known techniques ([A], [B], [C]). While the combination achieves good results, the paper would benefit from a deeper analysis of why this particular combination is effective and when it might fail.」

**避免的表述方式：**

- 「This paper has no contribution.」（过于绝对）
- 「This is just [X] with a minor tweak.」（过于轻蔑）
- 「Anyone could have done this.」（对人不对事）

---

## 模式 2：不清楚 (Lack of Clarity)

### 定义

论文的表达不清楚，导致审稿者（以及预期读者）无法理解论文的主要贡献、方法或结果。

### 常见症状

1. **读不懂**：多次阅读后仍不确定论文在说什么
2. **逻辑跳跃**：从问题到方法的推导有不合理的跳跃
3. **符号混乱**：同一个符号在不同地方代表不同意思，或符号未定义
4. **缺少直觉**：有公式但没有解释为什么这样设计
5. **结构混乱**：资讯出现的顺序不合理，读者需要反复翻阅

### 范例情境

**情境 A：符号灾难**
> 论文在 Section 3 定义了 $f_\theta$，在 Section 4 用 $f$ 表示同一个东西，然后在 Section 5 又用 $f$ 表示另一个函数。

**情境 B：动机缺失**
> 论文直接跳到方法描述，从未解释为什么现有方法不足、为什么需要新方法、新方法解决了什么现有方法解决不了的问题。

**情境 C：资讯流混乱**
> 论文在实验部分引入了方法中未提到的重要设计决定（如特殊的 data preprocessing），而方法部分的某些细节要到附录才能找到。

### 如何在审稿中指出

**推荐的表述方式：**

- 「The paper is difficult to follow in its current form. In particular, [specific section/paragraph] requires significant clarification. For instance, [specific example of unclear writing].」
- 「The notation is inconsistent — $f_\theta$ in Section 3 appears to refer to a different entity than $f$ in Section 5. I suggest the authors unify the notation throughout.」
- 「The motivation for the proposed approach is not clearly articulated. It would help to explicitly discuss the limitations of existing methods (e.g., [X, Y]) and how the proposed method addresses them.」

**避免的表述方式：**

- 「This paper is poorly written.」（太笼统，不指出具体问题）
- 「I cannot understand anything.」（可能是审稿者的问题而非论文的问题）

---

## 模式 3：效果弱 (Weak Results)

### 定义

论文声称的改进不显著、不可靠，或实验结果不足以支持论文的核心 claims。

### 常见症状

1. **改进不显著**：相对于 baselines 只有微小的改进，可能在误差范围内
2. **Cherry-picked results**：只展示方法表现好的情况，隐藏表现差的
3. **缺乏统计测试**：没有报告标准差或统计显著性
4. **与 claims 不匹配**：论文声称大幅改进，但数字显示改进很小
5. **不一致的结果**：在某些资料集上好，在另一些上不好，且没有解释

### 范例情境

**情境 A：统计不显著**
> 论文声称在三个资料集上都取得了 SOTA，但改进幅度分别为 0.1%、0.3%、0.2%，且没有报告标准差或 p-value。

**情境 B：选择性报告**
> 论文在 6 个资料集中的 4 个上取得改进，但只字未提在另外 2 个上表现更差。审稿者从附录的表格中发现了这一点。

**情境 C：Claims 过度**
> 摘要声称「significantly outperforms all existing methods」，但主表格显示只在特定设定下略好，在其他设定下与 baselines 持平或更差。

### 如何在审稿中指出

**推荐的表述方式：**

- 「The improvements over [baseline X] are marginal (e.g., 0.2% on Dataset A). Without statistical significance tests (e.g., paired t-test, bootstrap), it is unclear whether these improvements are meaningful.」
- 「I notice that the results on Datasets E and F (Appendix Table X) show degraded performance compared to the baseline. It would be important to discuss these cases and analyze when the method underperforms.」
- 「The claim in the abstract that the method 'significantly outperforms all existing methods' does not appear to be fully supported by the experimental results, particularly on [specific benchmarks].」

**避免的表述方式：**

- 「The results are not impressive.」（主观且不具体）
- 「The authors are cherry-picking.」（指控动机，而非指出事实）

---

## 模式 4：评估不全 (Incomplete Evaluation)

### 定义

论文的实验评估不够全面，缺少验证其 claims 所必需的关键实验、比较或分析。

### 常见症状

1. **缺少重要 baselines**：遗漏了该领域最新或最相关的对比方法
2. **资料集太少**：只在一两个资料集上实验，无法验证泛化性
3. **没有 ablation study**：方法有多个组件但不知道每个组件的贡献
4. **缺少分析**：只有数字没有洞见，不知道方法为什么有效或何时失效
5. **遗漏的评估指标**：只报告对自己有利的指标

### 范例情境

**情境 A：缺少 SOTA baseline**
> 一篇 2026 年的论文比较的最新 baseline 是 2023 年的方法，忽略了 2024-2025 年间发表的多个更强的方法。

**情境 B：缺少 ablation**
> 论文提出了一个包含三个新组件的方法（新 loss、新 architecture、新 training strategy），但只报告了完整方法的结果，没有分析每个组件的贡献。

**情境 C：单一资料集**
> 论文声称方法具有广泛的适用性，但只在一个资料集上进行了实验。

**情境 D：遗漏指标**
> 一篇生成模型的论文只报告 FID score，没有报告 diversity metrics（如 recall、coverage），而论文的方法可能牺牲了多样性来换取品质。

### 如何在审稿中指出

**推荐的表述方式：**

- 「Several important baselines are missing from the comparison, notably [X] (ICML 2025) and [Y] (NeurIPS 2025), which are directly relevant and have shown strong performance on the same benchmarks.」
- 「The paper would be significantly strengthened by an ablation study that isolates the contribution of each proposed component (the new loss, the architectural modification, and the training strategy).」
- 「Given the claim of broad applicability, evaluating on additional datasets from different domains (e.g., [specific suggestions]) would be necessary to support this claim.」
- 「Reporting only [metric A] may give an incomplete picture. I would suggest also reporting [metric B] and [metric C], which capture [aspect] that [metric A] does not.」

**避免的表述方式：**

- 「The experiments are insufficient.」（不指出缺少什么）
- 「The authors should run more experiments.」（不具体说明哪些实验）

---

## 模式 5：方法有缺 (Flawed Methodology)

### 定义

论文所提出的方法在技术层面有错误、不合理的假设，或存在根本性的方法论问题。

### 常见症状

1. **数学错误**：推导中有计算错误或逻辑错误
2. **不合理的假设**：方法依赖于在实际场景中不成立的假设
3. **Data leakage**：测试集的资讯泄漏到了训练过程中
4. **不公平比较**：自己的方法使用了 baselines 没有使用的额外资讯或资源
5. **忽略了已知的限制**：使用了已被证明在某些条件下失效的技术而未讨论

### 范例情境

**情境 A：数学错误**
> 论文在推导 Theorem 1 时，第三步的不等式方向反了。将 $\leq$ 改为 $\geq$ 后，整个定理的结论都需要改变。

**情境 B：Data leakage**
> 论文在 feature engineering 阶段使用了整个资料集（包括测试集）的统计资讯来做 normalization，导致测试集的资讯泄漏到了模型中。

**情境 C：不公平比较**
> 论文的方法使用了额外的未标记资料进行 pre-training，但所有 baselines 都只使用标记资料。在不考虑这个差异的情况下直接比较数字是不公平的。

**情境 D：隐含假设**
> 论文的方法假设资料是 i.i.d. 的，但实际应用场景（如时间序列或社交网路）明显违反了这个假设，论文未讨论此问题。

### 如何在审稿中指出

**推荐的表述方式：**

- 「I believe there may be an error in the derivation of Theorem 1. Specifically, in Eq. (5), the inequality should be reversed because [reason]. This would affect the main conclusion.」
- 「There appears to be a potential data leakage issue: the normalization in Section 3.2 uses statistics computed over the entire dataset including the test set. This could inflate the reported performance.」
- 「The comparison may not be entirely fair, as the proposed method uses additional unlabeled data for pre-training (Section 3.1) while the baselines do not. I would suggest either (a) providing baselines with the same pre-training data, or (b) clearly discussing this advantage.」
- 「The i.i.d. assumption (stated in Section 2) may not hold in the target application. It would be valuable to discuss the implications of violating this assumption and to test the method under non-i.i.d. conditions.」

**避免的表述方式：**

- 「The math is wrong.」（不具体指出哪里错了）
- 「The authors cheated by using test data.」（指控意图而非陈述观察）
- 「This method cannot work.」（过于绝对且不提供理由）

---

## 退稿模式的组合

一篇论文通常不会只触发一个退稿模式。常见的组合包括：

### 致命组合

- **贡献不足 + 效果弱**：没什么新意，结果也不好 -> 几乎确定被拒
- **方法有缺 + 效果弱**：方法有问题且结果不佳 -> 强烈拒稿
- **不清楚 + 方法有缺**：看不懂，而且看懂的部分有错 -> 强烈拒稿

### 可救组合

- **贡献好但写不清楚**：核心想法有价值但需要重写 -> borderline，视 rebuttal 而定
- **方法健全但评估不全**：技术上正确但需要更多实验 -> borderline，可以补做实验
- **效果好但贡献定位不清**：结果不错但没有解释清楚为什么 -> 可以在 rebuttal 中改善

### 审稿时的考量

- 触发一个致命模式（如方法有根本性错误）通常就足以构成拒稿理由
- 触发两个以上的非致命模式（如贡献不足 + 评估不全）加起来也可能构成拒稿
- 即使触发了某个模式，如果论文在其他维度极其出色，仍需综合考量
