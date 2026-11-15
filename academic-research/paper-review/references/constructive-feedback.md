# 建设性回馈写法指南

本文件提供撰写建设性学术审稿回馈的指南，包含如何批评而不伤人、具体与模糊回馈的对比，以及建议修改方向的模板。

---

## 核心原则

### 1. 对事不对人

审稿评论的对象是论文，而非作者。

| 对人（避免） | 对事（推荐） |
|-------------|-------------|
| 「The authors failed to...」 | 「The paper does not address...」 |
| 「The authors clearly don't understand...」 | 「The connection to [X] is not discussed...」 |
| 「The authors are lazy about...」 | 「Additional experiments on [X] would strengthen...」 |
| 「The authors made a mistake in...」 | 「There appears to be an issue with Eq. (3)...」 |

### 2. 指出问题的同时提供方向

每个 weakness 都应附带改进建议，即使只是方向性的。

**只指出问题（不完整）：**
> The paper lacks ablation studies.

**指出问题并提供方向（完整）：**
> The paper would benefit from ablation studies that isolate the contribution of each component. Specifically, comparing (1) the full model, (2) without the attention module, and (3) without the contrastive loss would help readers understand the importance of each design choice.

### 3. 使用缓和语气

学术审稿有一套约定俗成的缓和语气（hedging language）。

| 直接（可能显得攻击性） | 缓和（专业而友善） |
|----------------------|-------------------|
| 「This is wrong.」 | 「I believe there may be an issue with...」 |
| 「This doesn't work.」 | 「It is unclear whether this approach would generalize to...」 |
| 「This is trivial.」 | 「The contribution relative to [prior work] appears to be incremental.」 |
| 「The experiments are bad.」 | 「The experimental evaluation could be strengthened by...」 |

### 4. 承认不确定性

如果你不确定某个批评是否正确，要明确表达。

**好的做法：**
> I may be missing something, but it seems that Eq. (5) assumes independence between X and Y, which may not hold in practice. If this assumption is indeed required, it would be helpful to discuss its implications.

**不好的做法：**
> Eq. (5) is wrong because X and Y are not independent.

---

## 具体 vs 模糊回馈的对比

### 贡献相关

| 模糊（避免） | 具体（推荐） |
|-------------|-------------|
| 「The novelty is limited.」 | 「The main difference from [X] appears to be the use of [specific technique]. It would help to clarify why this modification is non-trivial and what challenges it addresses.」 |
| 「The contribution is not enough.」 | 「The paper presents [A] as a contribution, but [similar work Y] has explored a very similar idea. The paper would benefit from a detailed comparison with [Y] to highlight the unique aspects.」 |

### 写作相关

| 模糊（避免） | 具体（推荐） |
|-------------|-------------|
| 「The writing needs improvement.」 | 「Section 3.2 is difficult to follow. Specifically, the transition from Eq. (3) to Eq. (4) requires additional explanation of why [specific step] is valid.」 |
| 「The paper is hard to read.」 | 「The notation is inconsistent: $h$ denotes hidden states in Section 3 but is overloaded to mean hypothesis in Section 4. Using distinct symbols would improve readability.」 |

### 实验相关

| 模糊（避免） | 具体（推荐） |
|-------------|-------------|
| 「More experiments are needed.」 | 「Evaluating on [specific dataset] would test the method under [specific condition] and strengthen the generalization claim.」 |
| 「The baselines are outdated.」 | 「Recent methods such as [X] (ICML 2025) and [Y] (NeurIPS 2025) have achieved strong results on the same benchmarks and should be included for a fair comparison.」 |

### 方法相关

| 模糊（避免） | 具体（推荐） |
|-------------|-------------|
| 「The method has issues.」 | 「The optimization objective in Eq. (7) is non-convex, and the paper does not discuss convergence guarantees. Empirically demonstrating convergence (e.g., plotting the loss curve) would address this concern.」 |
| 「The assumptions are unrealistic.」 | 「Assumption 2 requires [specific condition], which is typically violated in [specific practical scenario]. Relaxing this assumption or empirically testing performance under violation would strengthen the work.」 |

---

## 审稿常用句型模板

### 表达优点

- 「A strength of this paper is [X], which [why it's good].」
- 「The paper makes a valuable contribution by [X].」
- 「I appreciate the thoroughness of [specific aspect].」
- 「The experimental setup is well-designed, particularly [specific aspect].」
- 「The writing is clear and the paper is easy to follow.」
- 「The problem addressed is important and timely.」

### 表达缺点（建设性）

- 「A concern is [X]. This could be addressed by [suggestion].」
- 「The paper would benefit from [X] to strengthen the [specific claim].」
- 「It is unclear [what/why/how]. Additional clarification would help.」
- 「One potential issue is [X]. It would be helpful to [suggestion].」
- 「While the approach is interesting, [X] raises a concern about [Y].」

### 提出问题

- 「Could the authors clarify [specific point]?」
- 「How does the method perform when [specific condition]?」
- 「What happens if [assumption] is violated?」
- 「Is there a reason why [specific baseline/dataset/metric] was not included?」
- 「How sensitive is the method to [specific hyperparameter]?」

### 提供建议

- 「I would suggest [specific action] to address this concern.」
- 「One way to strengthen this section would be to [specific suggestion].」
- 「Including [specific experiment/analysis] would help validate [specific claim].」
- 「The paper could be improved by [specific writing suggestion].」

### 表达不确定性

- 「I may be mistaken, but it appears that...」
- 「Unless I am missing something, [observation]...」
- 「If I understand correctly, [interpretation]. If so, [concern].」
- 「This is outside my core expertise, but [observation].」

---

## 不同情境的回馈策略

### 情境 1：你要拒稿但论文有可取之处

**策略**：先真诚地肯定优点，再具体说明问题，最后提供改进方向。

**范例：**
> The paper addresses an important problem and proposes an interesting approach. The idea of [X] is creative and the theoretical framework is well-motivated.
>
> However, I have several concerns that prevent me from recommending acceptance at this time:
>
> 1. [Major concern 1 + suggestion]
> 2. [Major concern 2 + suggestion]
>
> I believe this work has potential, and I encourage the authors to address these issues and resubmit.

### 情境 2：你要接受但论文有瑕疵

**策略**：清楚标注哪些是必须修改的，哪些是建议性的。

**范例：**
> Overall, this is a solid paper with a clear contribution. I recommend acceptance with the following revisions:
>
> **Required revisions (for camera-ready):**
> 1. [Issue that must be fixed]
>
> **Suggested improvements (optional but recommended):**
> 1. [Improvement that would make the paper stronger]

### 情境 3：你不确定方法是否正确

**策略**：描述你的理解，指出你疑惑的地方，用问句而非断言。

**范例：**
> If I understand correctly, the proof of Theorem 2 relies on the assumption that [X]. However, in the experimental setting described in Section 5, it seems that [Y] might not hold. Could the authors clarify whether the theorem still applies in this case? If not, how does this affect the practical guarantees?

### 情境 4：论文品质很差

**策略**：即使论文品质不佳，也保持专业和尊重。指出最核心的几个问题，不需要列出所有小问题。

**范例：**
> The paper attempts to address [problem], which is a relevant topic. However, there are several fundamental issues that need to be addressed before the paper is ready for publication:
>
> 1. [Most critical issue + why it matters + suggestion]
> 2. [Second critical issue + suggestion]
>
> I recommend the authors focus on addressing these core issues. Once the fundamental concerns are resolved, additional refinements in [writing/experiments] would also be beneficial.

---

## 回馈的结构化原则

### STAR 框架

对每个重要的回馈点，考虑使用以下结构：

- **S**ituation（情境）：指出论文中的具体位置
- **T**opic（主题）：说明你要评论什么
- **A**ssessment（评估）：你的判断是什么
- **R**ecommendation（建议）：你建议怎么改

**范例：**
> In Section 4.2 (Situation), the paper claims that the method achieves real-time performance (Topic). However, the reported inference time of 200ms per frame suggests this may not meet the common real-time threshold of 30 FPS (Assessment). I would suggest either adjusting the claim or providing optimization strategies that could bring the latency below 33ms (Recommendation).

### 优先级标记

在正式 review 中，区分不同重要性的回馈：

- **[Major]**：影响接受与否的重大问题
- **[Minor]**：不影响接受但建议改进的问题
- **[Nit]**：格式、typo 等极小的问题
- **[Question]**：需要作者回答的问题

---

## 审稿者常犯的错误

### 1. 只批评不肯定

即使是要被拒的论文，也值得被承认其优点。如果你找不到任何优点，可能是你没有认真读。

### 2. 要求作者做不可能的事

如「please compare with all existing methods」或「please prove that the method works in all cases」。要求应该是合理且具体的。

### 3. 把自己的研究方向强加于作者

「The paper should also consider [my favorite topic]」——除非真的相关，否则不要把自己的研究偏好当成论文的缺点。

### 4. 字数太少

「Reject. The paper is not good enough.」——这种 review 对作者毫无帮助，也不配被当作拒稿理由。

### 5. 前后矛盾

文字评论全是缺点但给了高分，或者文字评论很正面但给了低分。评分应与文字一致。

---

## 文化敏感度提醒

- 不要根据作者的英文写作品质推测其国籍或能力
- 不要因为论文使用了非标准的术语就认为作者不专业——可能是不同社群的用法
- 对于英文非母语的作者，区分「语言问题」和「逻辑问题」——前者可以修正，后者才是核心问题
- 保持客观，不要因为作者来自知名机构就给予优待，也不要因为来自不知名机构就更严格
