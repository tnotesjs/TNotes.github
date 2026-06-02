# [0011. excalidraw](https://github.com/tnotesjs/TNotes.github/tree/main/notes/0011.%20excalidraw)

<!-- region:toc -->

- [1. 🎯 本节内容](#1--本节内容)
- [2. 🫧 评价](#2--评价)
- [3. 💻 demos.1 - 共享画布功能](#3--demos1---共享画布功能)
- [4. 💻 demos.2 - 支持导入 mermaid 图表](#4--demos2---支持导入-mermaid-图表)
- [5. 🤔 为什么叫 excalidraw 这个名字呢？](#5--为什么叫-excalidraw-这个名字呢)
- [6. 🤔 都有哪些知名的 excalidraw skills？](#6--都有哪些知名的-excalidraw-skills)
  - [6.1. 记录回复：Qwen 3.7-Max](#61-记录回复qwen-37-max)
    - [如何使用这些 Skills ？](#如何使用这些-skills-)
- [7. 🔗 引用](#7--引用)

<!-- endregion:toc -->

## 1. 🎯 本节内容

- excalidraw 简介

## 2. 🫧 评价

🤩 🤩 🤩 这个项目太棒啦～～～

excalidraw 是一个开源的绘图工具，在接触到这个项目之前，一直在找 TNotes 笔记体系中绘图需求的解决方案。

在此（25.06）之前用的是 yuque 画板来实现绘图的需求，现在开始全盘转向 excalidraw 来实现。

个人最喜欢的几个核心亮点：

- 免费
- 页面和交互体验都极其优雅
- 支持 mermaid 解析，并且解析后的内容还支持可视化的二次编辑
- 有网页版和 vscode 插件版
  - 网页版可以直接在平板上实现绘图
  - vscode 插件版，可以将一个个作品以文件的形式存储下来，接下来在做一个笔记分享的时候，可以直接利用它来完成大部分的绘图工作。比如 leetcode 题解中如果需要作图说明，就可以用这个工具来实现。
  - 你可以直接复制 A（浏览器版、vscode 插件版） 画板内容粘贴到 B（vscode 插件版、浏览器版） 上，格式是完全兼容的。
- Share 功能
  - 你可以通过链接共享画板中的内容，这意味着你可以在电脑上打开网页，生成一个共享链接，然后在你的 iPad 上打开，对画板进行编辑。
  - 也可以将链接分享给其他朋友，它们可以通过链接实时看到你的画板内容，并且也可以协同编辑。

## 3. 💻 demos.1 - 共享画布功能

电脑和 iPad 共享画布：

![img](https://cdn.jsdelivr.net/gh/tnotesjs/imgs@main/2025-06-29-11-06-56.png)

比如上图中的 mark 是在 iPad 上通过 Apple pencil 写的字，红色的是在 PC 端任意位置双击鼠标键入的文本内容，矩形和箭头元素，是画板自带的一些组件。

## 4. 💻 demos.2 - 支持导入 mermaid 图表

- 支持解析 mermaid
- 支持修改字体
- 支持对解析后的内容进行二次编辑

::: swiper

![1. 输入 mermaid](https://cdn.jsdelivr.net/gh/tnotesjs/imgs@main/2025-06-29-11-19-17.png)

![2. 导入](https://cdn.jsdelivr.net/gh/tnotesjs/imgs@main/2025-06-29-11-21-41.png)

![3. 二次编辑](https://cdn.jsdelivr.net/gh/tnotesjs/imgs@main/2025-06-29-11-23-41.png)

:::

有些画板工具也支持导入 mermaid，但导入之后其实就变为了一张完整的图片，并不支持二次编辑。在导入后就是一张完整的图片，无法在对其中的内容进行二次编辑。

## 5. 🤔 为什么叫 excalidraw 这个名字呢？

Excalidraw 这个名字的由来很有趣，它结合了 "Excalibur"（亚瑟王的神剑） 和 "Draw"（绘画） 两个词，寓意是希望这个工具能像传说中的神剑一样强大、优雅，成为用户绘制草图时的“利器”。

Excalibur（誓约胜利之剑）：

- 在亚瑟王传说中，Excalibur 是一把象征力量与权威的神剑，只有真正的王者才能拔出它。
- 开发者借用这个名字，可能是想表达 Excalidraw 是一个“强大而优雅”的工具，能帮助用户轻松“斩断”复杂的设计问题。

Draw（绘画）：直接表明这是一个绘图工具，功能简单明了。

其他可能的联想：

- "Excali-" 发音类似 "excellent"（优秀的），暗示这是一个出色的绘图工具。
- 名字独特且易记，符合开源项目的命名风格（比如 Inkscape、GIMP 等）。

官方态度：虽然官方没有正式解释名字的起源，但社区普遍认可这个命名逻辑。开发者之一曾在访谈中提到，名字的灵感确实来自 Excalibur，希望工具能像神剑一样帮助用户“披荆斩棘”地创作。

## 6. 🤔 都有哪些知名的 excalidraw skills？

::: tip 提示

这个问题可以直接向 AI 咨询，获取到当下最新的信息，毕竟 excalidraw 这个项目在不断地迭代更新，新的功能和社区用户退出的配套技能也在不断地被开发出来。

可以这么问：

```
我正在使用 excalidraw 这个开源的绘图工具，想要接入 Agent 来帮助我更高效地使用这个工具。

请告诉我当下（2026.06）都有哪些知名的 excalidraw skills。

要求：完成联网搜索，给我返回一张表格，表格内容包括：skills 的获取链接和描述。
```

:::

### 6.1. 记录回复：Qwen 3.7-Max

尊敬的用户，您好！

首先需要说明的是，您提到的“ skills ”概念在传统的软件语境中通常被称为“插件（ Plugins ）”或“扩展（ Extensions ）”。但在您提到的“接入 Agent ”这一前沿语境下， Skills （技能）和 MCP Server （模型上下文协议服务器）确实是 2025 至 2026 年间 AI 代理（如 Claude Code 、 Cursor 、 GitHub Copilot Agent 等）生态中的标准术语。因此，您的问题本身并没有原则性错误，反而非常准确地切中了当下的技术趋势；为了严谨起见，我们一般将它们统称为 Agent Skills 或 MCP Tools ，以区别于 Excalidraw 原生的传统 UI 插件。

截至 2026 年 6 月，AI Agent 生态中已经涌现出多款非常成熟的 Excalidraw Skills 和 MCP Servers 。以下为您整理的知名 Excalidraw Skills / MCP 列表：

| Skill / MCP 名称 | 获取链接 | 描述 |
| :-- | :-- | :-- |
| excalidraw-diagram-skill (coleam00) | [GitHub 链接](https://github.com/coleam00/excalidraw-diagram-skill) | 专为 Claude Code 等编码 Agent 设计，能够根据代码库自动生成系统架构图，并输出为可编辑的 Excalidraw 视觉地图。 |
| excalidraw-mcp (Excalidraw 官方) | [GitHub 链接](https://github.com/excalidraw/excalidraw-mcp) | 官方支持的 MCP Server ，提供流式手绘图表生成能力，支持平滑的视口相机控制与交互式全屏编辑。 |
| Excalidraw+ MCP | [官方文档](https://plus.excalidraw.com/docs/mcp) | Excalidraw Plus 官方提供的 MCP 服务，允许 AI 客户端直接通过 Model Context Protocol 访问并操作用户的云端工作区。 |
| cc-excalidraw-skill (rnjn) | [GitHub 链接](https://github.com/rnjn/cc-excalidraw-skill) | 允许 Agent 以编程方式创建和编辑图表，当用户要求绘制流程图、架构图或线框图时自动触发。 |
| mcp_excalidraw (yctimlin) | [GitHub 链接](https://github.com/yctimlin/mcp_excalidraw) | 综合性的 MCP Server 与 Claude Code Skill ，提供基于 Node.js API 的实时画布同步、元素修改与导出功能。 |
| excalidraw-generation | [Smithery 链接](https://smithery.ai/skills/rhuss/excalidraw-generation) | 托管于 Smithery 平台的技能，专注于响应用户“生成手绘图表”或“绘制草图”的自然语言指令。 |
| agent-toolkit/skills/excalidraw (softaworks) | [GitHub 链接](https://github.com/softaworks/agent-toolkit/blob/main/skills/excalidraw/README.md) | 提供了一套优化的文件处理模式，专门解决 Excalidraw JSON 文件因体积过大而耗尽主 Agent 上下文预算的问题。 |
| Obsidian Excalidraw Skill | [知乎专栏介绍](https://zhuanlan.zhihu.com/p/2008887997408502501) | 专为在 Obsidian 笔记软件中使用 Excalidraw 插件的用户打造，实测效果极佳的绘图 Agent 技能。 |

#### 如何使用这些 Skills ？

1. 对于 Claude Code 或 OpenCode 用户：您通常可以在项目根目录下创建 `.claude/skills/` 文件夹，并将上述 Skill 的 `SKILL.md` 文件放入其中即可激活。
2. 对于 MCP 协议用户：如果您使用的是支持 MCP 的客户端（如 Cursor 、 Cherry Studio 等），可以直接在配置文件中添加对应的 MCP Server JSON 配置，即可让大模型直接调用绘图 API。

希望这些信息能帮助您的 Agent 更高效地绘制出精美的手绘风格图表！如果有具体环境的配置问题，欢迎随时向我提问。

## 7. 🔗 引用

- [excalidraw github][1]
- [excalidraw deepwiki][2]
- [mermaid 官网][3]
- [mermaid 在线网页版][4]
- [vscode 中的 mermaid 插件][5]

[1]: https://github.com/excalidraw/excalidraw
[2]: https://deepwiki.com/excalidraw/excalidraw
[3]: https://mermaid.js.org/
[4]: https://excalidraw.com/
[5]: https://marketplace.visualstudio.com/items?itemName=pomdtr.excalidraw-editor
