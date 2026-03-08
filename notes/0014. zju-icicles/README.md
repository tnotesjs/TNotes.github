# [0014. zju-icicles](https://github.com/tnotesjs/TNotes.github/tree/main/notes/0014.%20zju-icicles)

<!-- region:toc -->

- [1. 🎯 本节内容](#1--本节内容)
- [2. 🫧 评价](#2--评价)
- [3. 🤔 这个仓库中都包含哪些核心内容？](#3--这个仓库中都包含哪些核心内容)
- [4. 🤔 项目的核心脚本是？](#4--项目的核心脚本是)
- [5. 🤔 项目如何使用 GitHub Actions 实现自动化部署？](#5--项目如何使用-github-actions-实现自动化部署)
- [6. 🔗 引用](#6--引用)

<!-- endregion:toc -->

## 1. 🎯 本节内容

- zju-icicles

## 2. 🫧 评价

这个项目记录了浙大的一些课程学习资料，包含很多学科，有很多学习资料（pdf、txt、word、……）可一键下载，有需要可自行查阅官方文档。

## 3. 🤔 这个仓库中都包含哪些核心内容？

| 核心内容 | 简介 | 位置 |
| --- | --- | --- |
| 课程目录 | 存放各门课程的资料，每个课程有独立文件夹 | 仓库根目录下的各个课程文件夹 |
| 课程文件 | 实际的学习资料（笔记、试卷、教材等） | 各课程目录内 |

该项目收录了以下类型的课程资料：

- 选课攻略
- 电子版教材
- 平时作业答案
- 历年试卷
- 复习资料
- 开卷考试A4纸

![img](https://cdn.jsdelivr.net/gh/tnotesjs/imgs@main/2025-09-26-09-39-49.png)

具体都有哪些学习资料，可以自行访问仓库查阅。

## 4. 🤔 项目的核心脚本是？

核心是 `update.py` 脚本，它负责：

- 遍历课程目录
- 处理文件类型（文本文件和二进制文件使用不同的 URL 前缀）
- 生成 markdown 文档
- 将主 README.md 复制为 index.md

## 5. 🤔 项目如何使用 GitHub Actions 实现自动化部署？

项目使用 GitHub Actions 进行自动化：

- 在 master 分支推送时触发
- 安装 Python 依赖
- 运行 update.py 更新文档
- 自动部署到 GitHub Pages

## 6. 🔗 引用

- [zju-icicles - github][1]
- [zju-icicles - 官方文档][2]

[1]: https://github.com/QSCTech/zju-icicles
[2]: https://qsctech.github.io/zju-icicles/
