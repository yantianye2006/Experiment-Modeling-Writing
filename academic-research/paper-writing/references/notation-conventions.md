# 符号与用语一致性规范

## 数学符号规范

在整篇论文中，符号使用必须完全一致：

| 类型 | 惯例 | 范例 |
|------|------|------|
| 向量 | 小写粗体 | $\mathbf{x}$, $\mathbf{h}$ |
| 矩阵 | 大写粗体 | $\mathbf{W}$, $\mathbf{A}$ |
| 纯量 | 小写斜体 | $x$, $\alpha$, $\lambda$ |
| 集合 | 大写花体 | $\mathcal{X}$, $\mathcal{D}$ |
| 函数 | 小写斜体或特定符号 | $f(\cdot)$, $\mathcal{L}$ |
| 维度 | 大写斜体 | $N$, $D$, $T$ |
| 索引 | 小写斜体 | $i$, $j$, $k$ |

## 时态规范

| 语境 | 时态 | 范例 |
|------|------|------|
| 描述本文方法 | 现在式 | We propose / Our method processes |
| 描述实验过程 | 过去式 | We trained / We evaluated |
| 描述实验结果 | 现在式 | Table 1 shows / Our method achieves |
| 描述先前工作 | 过去式 | Smith et al. proposed / Previous work focused on |
| 描述普遍事实 | 现在式 | Transformers are widely used |

## 用词一致性

全文必须对同一概念使用同一词汇：

```
❌ 混用: feature / representation / embedding（在指同一件事时）
✅ 统一: 选择一个词，全文使用。首次出现时说明：
   "feature representation (hereafter referred to as 'feature')"
```
