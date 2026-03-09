# [0016. memorains](https://github.com/tnotesjs/TNotes.github/tree/main/notes/0016.%20memorains)

<!-- region:toc -->

- [1. 🎯 本节内容](#1--本节内容)
- [2. 🫧 评价](#2--评价)
- [3. 📺 bilibili - 我开源了自己开发的在线笔记软件 - 红鳞绿羽](#3--bilibili---我开源了自己开发的在线笔记软件---红鳞绿羽)
- [4. 🔗 引用](#4--引用)

<!-- endregion:toc -->

## 1. 🎯 本节内容

- memorains

## 2. 🫧 评价

- 这篇笔记记录了 B 站上刷到的一位 UP `红鳞绿羽` 做的一款开源笔记软件 memorains。
- memorains 的一些核心技术栈 React + Electron + NodeJS + Express
- 画板是基于 [excalidraw][3] 来实现的。
- 富文本功能是基于 [Quill][4] 来实现的。
- 其他核心功能：
  - 在线编辑
  - 在线协同
  - 客户端 - 基于 Electron 实现
  - 画板
  - 支持离线
  - 支持冲突处理
  - ……
- 跟自己目前在写的 `TNotes.xxx` 开源知识库的设计思路差异较大。由于作者也是在手写笔记工具，这一点和自己做的 TNotes 类似，其中应该会有一些可以借鉴的点，因此特地记录一下。

## 3. 📺 bilibili - 我开源了自己开发的在线笔记软件 - 红鳞绿羽

<B id="BV1baMhz3Ehj" />

以下内容引用自 UP 对此视频的简介：

```txt
这是我自己写的一个用了两年的在线笔记软件, 支持富文本和画板,支持多人协同编辑,这几天这这个软件开源了.

基本特点一览:
- 开源/自由

- 支持多种文档类型
  - 📝文本文档
  - 🖌️画布

- 本地/在线文档
 - 💾本地文档冲突解决合并
 - 🛜在线协作

- 🔐安全, 支持文档端对端加密

- 跨平台, 多端支持和部署
  - 客户端目前已经支持 web(pwa) 和桌面客户端
  - server 端 docker 部署

项目 Github 地址: https://github.com/redTreeOnWall/memorains
在线 Demo 地址: https://note.lirunlong.com/doc/client/
客户端(windows/linux)下载地址: https://github.com/redTreeOnWall/memorains/releases

视频快速索引:
00:00 开场
00:52 软件基本特点介绍
07:17 两种文档类型介绍
  - 07:28 富文本文档
  - 07:44 富文本文档
10:10 在线编辑和协作
13:44 本地离线编辑
23:52 文档端对端加密
28:22 软件原理讲解
31:37 后续计划
33:24 结尾 (开源项目地址)
```

## 4. 🔗 引用

- [UP 红鳞绿羽 - bilibili][1]
- [memorains - github - UP 的开源笔记软件][2]
- [excalidraw - github][3]
- [quill - github][4]

[1]: https://space.bilibili.com/39747309
[2]: https://github.com/redTreeOnWall/memorains
[3]: https://github.com/excalidraw/excalidraw
[4]: https://github.com/slab/quill
