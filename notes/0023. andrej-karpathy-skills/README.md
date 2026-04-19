# [0023. andrej-karpathy-skills](https://github.com/tnotesjs/TNotes.github/tree/main/notes/0023.%20andrej-karpathy-skills)

<!-- region:toc -->

- [1. 🎯 本节内容](#1--本节内容)
- [2. 🫧 评价](#2--评价)
- [3. 🤔 `andrej-karpathy-skills` 项目是什么？](#3--andrej-karpathy-skills-项目是什么)
- [4. 🔗 引用](#4--引用)

<!-- endregion:toc -->

## 1. 🎯 本节内容

- `andrej-karpathy-skills` 项目简介

## 2. 🫧 评价

`andrej-karpathy-skills` 核心就一个 `CLAUDE.md` 文件 => 这是一份减少常见 LLM 编码错误的行为指南。

在实际工作中试着用过，目前（26.04）使用的 coding agent 工具主要是 copilot，直接将 `CLAUDE.md` 文件中的内容丢到 `.github/copilot-instructions.md` 中，好像确实有点儿用。

## 3. 🤔 `andrej-karpathy-skills` 项目是什么？

`andrej-karpathy-skills` 是一个受 Andrej Karpathy 启发，旨在改善 AI 编码助手（如 Claude Code）行为的开源指南项目。

它的核心是一个 `CLAUDE.md` 文件，其中包含了四项核心原则，用于解决大型语言模型（LLM）在编写代码时常犯的错误：

1. 编码前思考：要求明确陈述假设，遇到歧义时主动询问，避免因错误假设而跑偏。
2. 简单优先：反对过度工程化，坚持用最少的代码解决问题，不添加未要求的抽象或功能。
3. 精准修改：编辑现有代码时，只修改必要部分，不擅自“优化”相邻代码或进行无关的格式化。
4. 目标驱动执行：将模糊的指令（如“修复 bug”）转化为可验证的成功标准（如“先写一个能复现 bug 的测试，再让它通过”），让 AI 能自主循环直至目标达成。

该项目提供了两种安装方式：推荐通过 Claude Code 插件安装，或直接将指南内容追加到项目的 `CLAUDE.md` 文件中。其核心理念是：与其告诉 AI 具体步骤，不如给它明确的成功标准，让它自己去循环达成。

总的来说，这是一个旨在让 AI 成为更谨慎、更简洁、更可控的编码伙伴的实用指南。

## 4. 🔗 引用

- [Karpathy-Inspired Claude Code Guidelines - github][1]
- [CLAUDE.md - github][2]

[1]: https://github.com/forrestchang/andrej-karpathy-skills/
[2]: https://github.com/multica-ai/andrej-karpathy-skills/blob/main/CLAUDE.md
