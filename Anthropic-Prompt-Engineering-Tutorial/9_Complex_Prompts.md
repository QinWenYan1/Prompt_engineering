# 📘 第9章 从零构建复杂提示 (Complex Prompts from Scratch)

> 来源说明：Anthropic Prompt Engineering Interactive Tutorial 第9章 | 本节涵盖：法律服务/金融服务实战、10 要素复杂提示模板、提示工程试错方法论

---

## 🧠 核心概念总览

- [*知识点1: 复杂提示的 10 大要素框架*](#id1)
- [*知识点2: 法律服务实战——宠物飓风法案例*](#id2)
- [*知识点3: 金融服务实战——税务条款解析*](#id3)
- [*知识点4: 提示工程的方法论*](#id4)

---

<a id="id1"></a>
## ✅ 知识点1: 复杂提示的 10 大要素框架

**理论**
教程为复杂提示总结了 10 个可组合的要素（带 `*` 为必选，其余按需选择）：

| # | 要素 | 是否必选 | 说明 |
|---|------|---------|------|
| 1 | **"User:" 开头** | ✅ | 所有 CLAUDEMESSAGES() 提示必须以此开头 |
| 2 | **任务上下文** | ✅ | 赋予 Claude 角色和总体目标，如 `You are an expert lawyer.` |
| 3 | **语气上下文** | 可选 | 告知 Claude 应使用的语气 |
| 4 | **输入数据（XML标签包裹）** | 可选 | 需要处理的数据放入 `<tag>{{VARIABLE}}</tag>` |
| 5 | **示例（Examples）** | 强烈推荐 | 至少一个理想回应的示例，用 `<example>` 标签包裹。**"示例可能是知识工作中让 Claude 按预期行为的最有效工具"** |
| 6 | **详细任务描述与规则** | ✅ | 展开任务要求，提供"退路"（不知道答案时怎么做） |
| 7 | **即时任务描述** | 推荐 | 在长提示末尾"提醒"Claude 当前要做什么 |
| 8 | **逐步思考** | 可选 | `Before you answer, pull out the most relevant quotes...` |
| 9 | **输出格式** | 可选 | 如 `Put your response in <answer> tags.` |
| 10 | **预填充回复** | 可选 | 在 `Assistant:` 后预填引导内容 |

**注意点**
- 💡 **理解技巧**：这 10 个要素本质上是把 Ch1-Ch8 的所有技术整合到一个提示模板中——从格式（Ch1）、清晰表达（Ch2）、角色（Ch3）、XML（Ch4）、格式化（Ch5）、思考（Ch6）、示例（Ch7）、防幻觉（Ch8）——全部到位
- ⚠️ 要素之间顺序可以调整，教程强调**"提示工程在于科学的试错"**

---

<a id="id2"></a>
## ✅ 知识点2: 法律服务实战——宠物飓风法案例

**理论**
完整法律服务提示模板：

```
User: You are an expert lawyer.                             ← 要素2: 任务上下文

Here is some research that's been compiled.                 ← 要素4: 输入数据
<legal_research>
{{LEGAL_RESEARCH}}
</legal_research>

<examples>                                                   ← 要素5: 示例
<example>
The statute of limitations expires after 10 years. [3].
</example>
</examples>

Write a clear, concise answer to this question:             ← 要素6: 任务描述与规则
<question>{{QUESTION}}</question>
If there is not sufficient information, write 
"Sorry, I do not have sufficient information..."

Before you answer, pull out the most relevant quotes        ← 要素8: 逐步思考
in <relevant_quotes> tags.

Put your response in <answer> tags.                         ← 要素9: 输出格式
Assistant: <relevant_quotes>                                ← 要素10: 预填充
```

**输入变量**：
- `{{QUESTION}}` = "Are there any laws about what to do with pets during a hurricane?"
- `{{LEGAL_RESEARCH}}` = 3 条搜索结果（动物健康专利诉讼、兽医牙科执业、Katrina 飓风后宠物疏散立法）

**注意点**
- 💡 这个模板展示了**工厂流水线**式的提示设计——固定框架 + 可变输入 + 引用格式规范
- ⚠️ 长文档时最佳实践是将问题放在文档**底部**，但教程为可读性将问题放在了顶部

---

<a id="id3"></a>
## ✅ 知识点3: 金融服务实战——税务条款解析

**理论**
- 金融服务是**练习**（Exercises），要求学习者根据同样的 10 要素框架自己构建提示
- 场景：分析美国《国内收入法典》第 83 条（Section 83），回答 "How long do I have to make an 83b election?"
- 正确答案：**30 天内**（Section 83(b)(2) 规定选举须在转让后 30 天内作出）
- 输入数据是一份完整的税法条款文本（约数千词），Claude 需要从中提取一句话的答案

**注意点**
- 💡 这个练习的核心挑战是**从长文本中找精确答案**——结合了 Ch4（XML分隔）、Ch6（逐步思考）、Ch7（示例引导）、Ch8（证据先行）
- 🔄 金融场景展现的是**结构化信息的精确提取**，而法律场景展现的是**多源信息的综合分析**——两个行业对提示设计的侧重点不同

---

<a id="id4"></a>
## ✅ 知识点4: 提示工程的方法论

**理论**
教程在结尾提供了 8 条后续学习路径：

1. 📚 从 [Anthropic Cookbook](https://docs.anthropic.com) 学习生产级提示词示例
2. 📖 阅读 Anthropic 提示指南
3. 💡 查看 Prompt Library 获取灵感
4. 🤖 尝试 Metaprompt——让 Claude 为你写提示模板
5. 💬 在 Discord 服务器中提问
6. ⚙️ 了解 API 参数：temperature、max_tokens 等
7. 📄 阅读提示工程学术论文
8. 🛠️ 练习构建提示词，让 Claude 做你感兴趣的事

教程结语：
> "如果你完成了所有练习，你已跻身顶尖 0.1% 的 LLM 驾驭者。提示工程是一门新兴学科，保持开放心态——**你完全有可能发现下一个伟大的提示技巧。**"

**注意点**
- 💡 **核心方法论**：提示工程不是死记硬背——从逐步思考到角色分配到使用示例再到清晰写作，这些技巧可以**被融合、重组并以无数方式改编**
- 🔄 **关键建议**：为大型复杂提示开发测试用例，尝试多种结构——很少是纯粹公式化的

---

## 🔑 核心要点总结
1. 复杂提示 = 10 要素的灵活组合，不是死板模板
2. 示例（要素5）是最有效的知识工作提示工具
3. 法律 vs 金融：不同行业对提示结构的侧重点不同
4. 提示工程是**试错科学**——测试用例 + 结构实验 = 好提示

## 📌 考试速记版
- **10 要素速记**：User开头 → 角色 → 语气 → 数据(XML) → 示例 → 规则+退路 → 即时任务 → 思考 → 格式 → 预填充
- **核心原则**：试错、测试、重组
- **终极建议**：你可能就是发现下一个伟大提示技巧的人
