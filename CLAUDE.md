# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is a **documentation/content** repository organizing bilingual (Chinese 简体中文 + English) course notes on prompt engineering. There is no build system, test suite, or linting. Licensed under MIT.

## Repository Architecture

Three-level README hierarchy:
- **Root `README.md`** — meta-navigation hub: course overview, side-by-side comparison table, learning paths, repo tree
- **Course `README.md`** — lesson/chapter index with one-line summaries (table format)
- **Individual notes** — full structured content per lesson/chapter

Each course README ends with a cross-link to the root comparison table:
```
> 💡 想知道这门课和[other course]的区别？→ 见 [根目录 README 对比表](../README.md#-两门课程的区别)
```

## Two Course Note Structures

The two courses use **different structural patterns**. Match the existing pattern when editing.

### Anthropic Tutorial notes (`Anthropic-Prompt-Engineering-Tutorial/`)

```
# 📘 第N章 中文标题 (English Title)

> 来源说明：Anthropic Prompt Engineering Interactive Tutorial 第N章 | 本节涵盖：topic1、topic2、topic3

---

## 🧠 核心概念总览                  ← anchor list linking to each 知识点
- [*知识点1: Title*](#id1)
- [*知识点2: Title*](#id2)

---

<a id="id1"></a>                        ← anchor target (no blank line before heading)
## ✅ 知识点N: Title
  content with **注意点** callouts (💡/⚠️), prompt examples in code fences

---

## 🔑 核心要点总结
1. numbered summary
```

Key conventions:
- Anchor IDs are sequential: `id1`, `id2`, ... — must match overview list exactly
- `<a id="idN"></a>` sits directly above `## ✅ 知识点N:` with no blank line between them
- Callouts use emoji: 💡 tip, ⚠️ warning
- Images: `![alt text](images/N.png)` — numbered PNGs in `images/` subdirectory

### Prompting-for-Everyone notes (`Prompting-for-Everyone/`)

```
# 📘 NN 中文标题 (English Title)

> 来源：Andrew Ng | Module X: Module Name | 课时 N/M | ~N 分钟

---

## 🧠 核心概念总览
- [*知识点1: Title*](#id1)

---

## 🧠 本课核心                          ← unlike Anthropic notes: a summary paragraph FIRST
  one-paragraph overview of the lesson's main insight

---

<a id="id1"></a>
## ✅ 知识点N: Title
  content with **注意点** callouts, tables, prompt examples

---

## 🔑 本课核心要点
1. numbered takeaways

## 📌 实践速查                         ← unique to this course: quick-reference prompt templates
  reusable prompt templates in code fences
```

Key differences from Anthropic notes:
- **`## 🧠 本课核心`** summary paragraph after the overview (Anthropic notes skip this)
- **`## 📌 实践速查`** quick-reference section at the end (Anthropic notes lack this)
- Source line uses `来源：Andrew Ng | Module ... | 课时 ...` format
- File naming: `NN_Title_Name.md` (zero-padded two digits, 01–18)

## File Naming

| Course | Pattern | Examples |
|--------|---------|----------|
| Anthropic | `N_Title_Name.md` for chapters, `X_Title.md` for appendixes | `1_Basic_Prompt_Structure.md`, `A_Chaining_Prompts.md` |
| Prompting-for-Everyone | `NN_Title_Name.md` (zero-padded, 01–18) | `01_AI_Novice_Power_User.md`, `17_Data_Analysis.md` |

## Content Conventions

- **Language**: Chinese (简体中文) with English terms in parentheses, e.g. `上下文 (Context)`
- **Images**: stored in course-level `images/` directories, referenced as `images/N.png`
- **Prompt examples**: in code fences, typically without a language tag
- **Callouts**: `> 💡` for tips, `> ⚠️` for warnings, `**注意点**` for bullet-point caveats
- **Tables**: centered column alignment (`|------|`), used sparingly in notes, never in Anthropic overview sections

## Custom Skills

Three skills in `~/.claude/skills/` are designed for this type of content (not registered in the Skill tool — read them from disk and apply manually):

| Skill | Purpose |
|-------|---------|
| `chapter-nav-readme` | Generate chapter/module-level README with 核心+难点 blocks per section |
| `course-root-readme` | Generate root-level meta-navigation README linking multiple courses |
| `course-notes-generator` | Generate structured individual course notes from source materials |
