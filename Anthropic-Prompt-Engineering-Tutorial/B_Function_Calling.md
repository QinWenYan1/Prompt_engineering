# 📘 附录B 函数调用 (Function Calling)

> 来源说明：Anthropic Prompt Engineering Interactive Tutorial 附录 | 本节涵盖：函数调用概念、当前状态

---

## 🧠 核心概念总览

- [🔗 返回课程导航](./README.md)

---

## ⚠️ 注意

本章节内容尚未正式发布。Google Sheets 教程中此页面为占位状态，原文说明：

> "Our function calling system and syntax is due for improvements in the near future. We will have a full function calling lesson up when those improvements have been implemented."

当前可参考的资源：

| 资源 | 链接 |
|------|------|
| **函数调用文档** | [Anthropic Function Calling Docs](https://docs.anthropic.com) |
| **Cookbook 示例** | [Anthropic Cookbook](https://github.com/anthropics/anthropic-cookbook) |
| **Tool Use 仓库** | [Anthropic Tool Use Repo](https://github.com/anthropics) |

---

## 🔗 关联内容

函数调用模式已在附录A（提示链）的第4个示例中有所展示——让 Claude 从文本中提取人名（第1步「函数」），再将结果传给下一个提示（第2步）做排序处理。本质上就是：**让 Claude 执行某个函数 → 取结果 → 做后续处理**，运作方式与提示链中的变量替换完全相同。
