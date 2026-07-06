# 📘 第2章 清晰直接地表达 (Being Clear and Direct)

> 来源说明：Anthropic Prompt Engineering Interactive Tutorial 第2章 | 本节涵盖：清晰直接提示的核心原则、跳过前导语、强制确定性回答

---

## 🧠 核心概念总览

- [*知识点1: 清晰直接指令的核心原则*](#id1)
- [*知识点2: 黄金法则——用同事测试你的提示*](#id2)
- [*知识点3: 跳过前导语——俳句示例*](#id3)
- [*知识点4: 强制确定答案——篮球GOAT示例*](#id4)

---

<a id="id1"></a>
## ✅ 知识点1: 清晰直接指令的核心原则

**理论**
- Claude 对清晰、直接的指令(`clear and direct instructions`)反应最好
- 教程将 Claude 类比为**刚入职的新员工**——必须被明确告知要做什么，不能假设它会自己猜出来
- 如果指令模糊，Claude 会像人一样给出泛泛而谈的错误回答
- **这不是模型能力问题，而是提示设计问题**

**注意点**
- 💡 把 Claude 想象成一个非常聪明但**第一次见你**的实习生——它什么都能做，但需要你告诉它到底要什么

---

<a id="id2"></a>
## ✅ 知识点2: 黄金法则——用同事测试你的提示

**理论**
教程提出「清晰提示的黄金法则」（`Golden Rule of Clear Prompting`）：

> **把你的提示给同事或朋友看，让他们根据提示执行任务。如果他们感到困惑，Claude 很可能也会困惑。**

- 这是最实用的自查方法——人的困惑 = 模型的困惑
- 不需要任何技术背景就能验证提示的清晰度

**注意点**
- 💡 提示工程中最简单也最被低估的调试技巧——不需要跑模型，让旁边的人读一遍就行

---

<a id="id3"></a>
## ✅ 知识点3: 跳过前导语——俳句示例

**理论**

| 版本 | 提示 | 结果 |
|------|------|------|
| 普通版 | `User: Write a haiku about robots.` | Claude 加前导语 "Here is a haiku about robots:" |
| 改进版 | `User: Write a haiku about robots. Skip the preamble; go straight into the poem.` | Claude 直接输出诗歌 |

- Claude 默认会「礼貌地」加上过渡语，如果不需要，直接说「不要」

**教材示例/公式**
```
User: Write a haiku about robots. Skip the preamble; go straight into the poem.
```

**注意点**
- 🔄 **知识关联**：第5章会介绍另一种方法——用 XML 标签包裹输出内容来分离正文与废话

---

<a id="id4"></a>
## ✅ 知识点4: 强制确定答案——篮球GOAT示例

**理论**

| 版本 | 提示 | 结果 |
|------|------|------|
| 模糊版 | `User: Who is the best basketball player of all time?` | Claude 列举多位候选人，不给出明确答案 |
| 明确版 | `User: Who is the best basketball player of all time? Yes, there are differing opinions, but if you absolutely had to pick one player, who would it be?` | Claude 被迫选一个 |

- Claude 默认在争议性问题上保持中立
- 如果确实需要一个确定答案，必须明确要求——"即使有争议，你必须选一个"

**教材示例/公式**
```
User: Who is the best basketball player of all time? Yes, there are differing 
opinions, but if you absolutely had to pick one player, who would it be?
```

**注意点**
- ⚠️ 强制选择会牺牲客观性，只适用于需要决策/推荐的场景
- 💡 "if you absolutely had to pick one" 相当于给 Claude 一个「允许」——我知道有争议，但我需要你选一个

---

## 🔑 核心要点总结
1. Claude 不会读心——清晰直接的指令是好结果的必要条件
2. 黄金法则：同事能理解的提示，Claude 才能理解
3. 不需要的前导语可以通过直接要求来消除
4. 争议问题需要明确告诉 Claude 「必须选一个」，否则它会保持中立

## 📌 考试速记版
- **清晰提示黄金法则**：给人看 → 人困惑 = Claude 困惑
- **跳过前导语**：`Skip the preamble; go straight into the poem.`
- **强制选择**：`if you absolutely had to pick one, who would it be?`
- **易混淆**：客观中立（好事）vs 回避回答（需要改进提示）
