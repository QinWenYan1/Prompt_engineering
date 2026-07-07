# Prompt Engineering 学习笔记

> 整理了两份互补的 Prompt Engineering 课程笔记——一份教你**怎么写** prompt，一份教你**什么时候用什么**策略。

---

## 📚 课程总览

| | Anthropic 提示工程教程 | AI Prompting for Everyone |
|------|---------------------|--------------------------|
| **作者** | Anthropic 官方 | Andrew Ng @ DeepLearning.AI |
| **形式** | Google Sheets 交互式教程 | 视频课程（含 transcript） |
| **定位** | 面向 API 开发者 | 面向所有人 |
| **笔记数** | 9 章 + 3 附录 | 18 课 |
| **语言** | 中英双语 | 中英双语 |
| **入口** | [→ 进入目录](./Anthropic-Prompt-Engineering-Tutorial/README.md) | [→ 进入目录](./Prompting-for-Everyone/README.md) |

---

## 🆚 两门课程的区别

| | Anthropic 课程 | Andrew Ng 课程 |
|------|--------------|-------------|
| **定位** | 面向 API 开发者，技术深度高 | 面向所有人，强调实用思维 |
| **内容** | 9 章：提示结构、角色、XML、格式化、思考链、示例、防幻觉、复杂提示 | 18 课：信息获取、思想伙伴、多媒体代码 |
| **风格** | 技术文档式，大量 prompt 模板 | 场景驱动，大量 Andrew Ng 个人案例 |
| **互补性** | 教你**怎么写**复杂 prompt | 教你**什么时候用什么** prompt 策略 |

---

## 🚀 建议学习路径

**如果你刚入门** → 从 Andrew Ng 课程开始。它用日常场景帮你建立「AI 思维」，不需要技术背景。

**如果你要调 API / 做开发** → 从 Anthropic 教程开始。它直接教你 prompt 的结构化写法（XML 标签、角色分配、格式化输出）。

**如果你想全面掌握** → 两门都看，它们是互补的——Andrew Ng 告诉你「何时用」，Anthropic 告诉你「怎么写」。

---

## 📂 仓库结构

```
.
├── Anthropic-Prompt-Engineering-Tutorial/   # Anthropic 官方教程笔记
│   ├── README.md                            #   课程导航 + 资源链接
│   ├── 1_Basic_Prompt_Structure.md          #   9 章核心内容
│   ├── ...
│   └── C_Search_and_Retrieval.md            #   3 篇附录
│
├── Prompting-for-Everyone/                  # Andrew Ng 课程笔记
│   ├── README.md                            #   课程导航 + 资源链接
│   ├── 01_AI_Novice_Power_User.md           #   18 课结构化笔记
│   ├── ...
│   └── 18_Conclusion.md
│
├── README.md                                #   你在这里
└── LICENSE                                  #   MIT
```

---

## 📄 许可

本仓库内容采用 [MIT License](./LICENSE) 开源。
