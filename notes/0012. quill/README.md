# [0012. quill](https://github.com/tnotesjs/TNotes.github/tree/main/notes/0012.%20quill)

<!-- region:toc -->

- [1. 🎯 本节内容](#1--本节内容)
- [2. 🫧 评价](#2--评价)
- [3. 🤔 Quill 是什么？](#3--quill-是什么)
- [4. 🤔 Quill 的核心特性都有哪些？](#4--quill-的核心特性都有哪些)
  - [4.1. 专为开发者设计 (API Driven)](#41-专为开发者设计-api-driven)
  - [4.2. 模块化架构 (Modular Architecture)](#42-模块化架构-modular-architecture)
  - [4.3. 跨平台兼容](#43-跨平台兼容)
  - [4.4. 主题支持](#44-主题支持)
- [5. 💻 demos.1 - Quill Quick Start](#5--demos1---quill-quick-start)
- [6. 🔗 引用](#6--引用)

<!-- endregion:toc -->

## 1. 🎯 本节内容

- Quill

## 2. 🫧 评价

Quill 是一个强大的开源富文本编辑器，据说有不少在线的富文本编辑器都是基于 Quill 实现的。

## 3. 🤔 Quill 是什么？

Quill 是 GitHub 上一个非常流行且强大的开源富文本编辑器（Rich Text Editor）项目。它以其现代化的架构、高度的可扩展性以及优秀的跨平台兼容性而著称。

以下是关于该项目的详细介绍：

- 项目名称: Quill
- 核心定位: 一个为兼容性和扩展性而构建的现代所见即所得（WYSIWYG）编辑器。
- 维护者: 目前由 Slab 公司开发和维护。
- 许可证: BSD 许可（允许在个人和商业项目中免费使用）。
- 流行度: 在 GitHub 上拥有超过 20k+ 的 Star，是前端领域最主流的富文本编辑器之一。
- 语言: 主要使用 TypeScript 开发，提供了良好的类型定义。
- 数据结构: 内部使用一种称为 Delta 的操作序列来描述文档内容和变更，这是实现协同编辑和撤销/重做功能的基础。

生态系统与集成：由于 Quill 的流行，社区为其开发了丰富的框架封装版本，方便在不同技术栈中使用。

- React: `react-quill`
- Vue: `vue-quill-editor` (及多个社区维护版本)
- Angular: `ngx-quill`
- 其他: 支持 jQuery 原生调用，也可轻松集成到各种后端 CMS 系统中。

适用场景：

- 内容管理系统 (CMS): 博客文章、新闻发布。
- 在线协作工具: 文档协同编辑、笔记应用。
- 邮件客户端: 富文本邮件撰写。
- 教育平台: 作业提交、论坛讨论。
- 即时通讯: 需要富文本消息的场景。

## 4. 🤔 Quill 的核心特性都有哪些？

### 4.1. 专为开发者设计 (API Driven)

Quill 不仅仅是一个 UI 组件，它提供了一套完整的 API 来精细控制编辑器的内容、变更和事件。

- 数据格式: 输入和输出均支持标准的 JSON 格式（称为 Delta 格式），这使得内容的保存、传输和协同编辑变得非常容易和确定性强。
- 细粒度控制: 开发者可以通过 API 精确地插入文本、删除内容、应用格式或监听用户的每一次操作。

### 4.2. 模块化架构 (Modular Architecture)

Quill 的核心非常轻量，其大部分功能（如工具栏、历史记录、键盘绑定等）都是通过模块实现的。

- 按需定制: 你可以只引入需要的模块，从而减小打包体积。
- 高度可扩展: 开发者可以编写自定义模块（Blots）来添加全新的功能，例如嵌入视频、自定义图片处理、数学公式等，而无需修改核心代码。

### 4.3. 跨平台兼容

- 支持所有现代浏览器（桌面端、平板和手机）。
- 在不同设备和操作系统上提供一致的编辑体验。

### 4.4. 主题支持

内置了两种主要主题，开箱即用：

- Snow: 经典的顶部工具栏样式，类似 Word 的界面，最常用。
- Bubble: 气泡式工具栏，选中文字后浮动显示，适合评论或轻量级编辑场景。

## 5. 💻 demos.1 - Quill Quick Start

快速上手非常简单，只需引入两个核心文件即可体验：

- `quill.snow.css` 是 quill 样式主题 css 文件
- `quill.js` 是 quill 核心逻辑 js 文件

::: code-group

<<< ./demos/1/1.html {9-13,32-33}

:::

最终效果：

![img](https://cdn.jsdelivr.net/gh/tnotesjs/imgs@main/2025-06-29-10-46-44.png)

## 6. 🔗 引用

- [quill - github][1]
- [quill - 官网][2]
- [quill - docs][3]

[1]: https://github.com/slab/quill
[2]: https://quilljs.com/
[3]: https://quilljs.com/docs/quickstart
