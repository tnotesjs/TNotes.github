# [0010. zreadai](https://github.com/tnotesjs/TNotes.github/tree/main/notes/0010.%20zreadai)

<!-- region:toc -->

- [1. 🎯 本节内容](#1--本节内容)
- [2. 🫧 评价](#2--评价)
- [3. 🤔 Zread.ai 是什么？](#3--zreadai-是什么)
- [4. 🤔 zreadai 有对应的 Chrome 插件吗？](#4--zreadai-有对应的-chrome-插件吗)
- [5. 🔗 引用](#5--引用)

<!-- endregion:toc -->

## 1. 🎯 本节内容

- zreadai

## 2. 🫧 评价

- zreadai 是和 deepwiki 类似的一个 Github 项目源码学习工具。
- zreadai 是国内的智谱团队研发的，文档默认是中文，对国内用户更加友好。
- 对于一些技术问题的回复，效果感觉没 deepwiki 好。

## 3. 🤔 Zread.ai 是什么？

- **Zread.ai**
  - **Zread.ai**，这是由智谱 AI（Zhipu AI）在 2025 年 7 月下旬推出的一款面向开发者的 **AI 驱动的开源项目解读工具**。
  - ![图 0](https://cdn.jsdelivr.net/gh/tnotesjs/imgs@main/2025-07-25-23-09-13.png)
  - Zread.AI 的功能类似于 [Cognition][4] 推出的 DeepWiki，用法也非常类似，优点是支持中文。
  - 支持一键生成技术文档、架构图、模块解析等内容。
  - 目前已经索引了大部分热门开源项目，对于冷门代码仓库，你可以申请发起索引请求。
- 基本用法：
  - 方式一：将 github 仓库地址中的 `github.com` 改为 `zread.ai`
    - 比如：`https://github.com/excalidraw/excalidraw`
    - 改为：`https://zread.ai/excalidraw/excalidraw`
    - 回到仓库：这意味着如果你正在阅读一篇由 zread.ai 生成的 github 项目说明文档时，你也可以逆向操作 `zread.ai` -> `github.com`，快速定位到源仓库。
  - 方式二：进入 [zread.ai 官网][1] 将 github 仓库地址复制到输入框中，点击搜索。
    - ![图 3](https://cdn.jsdelivr.net/gh/tnotesjs/imgs@main/2025-07-25-23-21-19.png)
    - 如果你正在搜索的库还没有被索引，需要自行手动发起索引请求，就现在（25.07）体验来看，排队的时间还是比较长的。
    - ![图 4](https://cdn.jsdelivr.net/gh/tnotesjs/imgs@main/2025-07-26-13-17-42.png)
- 核心功能：

| **功能** | **说明** |
| --- | --- |
| **一键生成项目手册** | 将 GitHub 链接转为结构化文档，含目录、架构图、使用指南等（支持中文） |
| **Buzz 社区动态聚合** | 展示项目的 commits、issues、社区评价等实时动态 |
| **多仓库对比** | 支持横向比较多个项目的技术方案、性能差异等 |
| **私有项目支持** | 付费用户可上传私有代码库生成内部文档（非开源） |

## 4. 🤔 zreadai 有对应的 Chrome 插件吗？

- [zread][2] 是一款 zreadai 的自动跳转的插件。
- 当你打开一个 github 开源项目的时候，它会自动生成一个 zreadai 的跳转链接。
- 这里以 excalidraw 为例：
  - https://github.com/excalidraw/excalidraw
    - excalidraw github 仓库地址
  - ![图 1](https://cdn.jsdelivr.net/gh/tnotesjs/imgs@main/2025-07-25-23-11-49.png)
  - https://zread.ai/excalidraw/excalidraw
    - 点击链接之后，跳转到的 zreadai 生成的文档地址。
    - ![图 2](https://cdn.jsdelivr.net/gh/tnotesjs/imgs@main/2025-07-25-23-13-29.png)

## 5. 🔗 引用

- [zreadai -> 官网][1]
- [zread -> Chrome 插件][2]
- [oschina -> 智谱 Z.ai 推出开源项目阅读工具 Zread.ai][3]
- [Cognition AI][4]
  - Devin 的开发公司

[1]: https://zread.ai
[2]: https://chromewebstore.google.com/detail/zread/paegcagokmhdjmeekgjffgblieejddkp
[3]: https://www.oschina.net/news/361635
[4]: https://cognition.ai/
