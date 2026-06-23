# [0027. MinerU](https://github.com/tnotesjs/TNotes.github/tree/main/notes/0027.%20MinerU)

<!-- region:toc -->

- [1. 本节内容](#1-本节内容)
- [2. 评价](#2-评价)
- [3. 请详细介绍一下 MinerU 这个项目【AI】](#3-请详细介绍一下-mineru-这个项目ai)
  - [3.1. MinerU 是什么？](#31-mineru-是什么)
  - [3.2. 它主要解决什么问题？](#32-它主要解决什么问题)
  - [3.3. 核心能力](#33-核心能力)
  - [3.4. 大致工作流程](#34-大致工作流程)
  - [3.5. 后端模式怎么理解？](#35-后端模式怎么理解)
  - [3.6. 安装与基本使用](#36-安装与基本使用)
  - [3.7. 输出文件长什么样？](#37-输出文件长什么样)
  - [3.8. 适合哪些场景？](#38-适合哪些场景)
  - [3.9. 项目活跃度与版本现状](#39-项目活跃度与版本现状)
  - [3.10. 注意点与限制](#310-注意点与限制)
  - [3.11. 总结](#311-总结)
- [4. 引用](#4-引用)

<!-- endregion:toc -->

## 1. 本节内容

- MinerU 项目简介

## 2. 评价

在个人的日常使用中，MinerU 的定位非常简单，它只解决一个问题：“学习资料 -> Markdown”的转换问题。

在个人维护的 TNotes.xxx 系列知识库中，笔记正好就是以 Markdown 的形式来记录的。

使用流程也非常简单：

1. 准备好需要的“学习资料”，这里的学习资料可以是 PDF、Word、PPT、Excel、图片、网页 URL
2. 将学习资料丢给 MinerU 解析
   1. 你可以到 [MinerU 官网][2] 直接在线体验
   2. 也可以下载官方的客户端到本地运行
3. 导出解析结果即可

## 3. 请详细介绍一下 MinerU 这个项目【AI】

下面按“它是什么、能做什么、怎么实现、怎么用、适合谁、注意点”来介绍。

### 3.1. MinerU 是什么？

**MinerU 是 OpenDataLab 开源的文档解析引擎**，目标是把复杂文档转换成适合 **LLM、RAG、Agent 工作流**使用的结构化 Markdown / JSON。它支持 `PDF`、图片、`DOCX`、`PPTX`、`XLSX` 等输入，并把文档内容按阅读顺序解析成机器可读结果。官方 README 也把它定位为面向 “LLM · RAG · Agent workflows” 的高精度文档解析引擎。([github.com](https://github.com/opendatalab/MinerU))

它不是简单 OCR。普通 OCR 只把页面“识别成文字”，但 MinerU 更关注**文档结构还原**：标题、段落、表格、公式、图片、脚注、页眉页脚、多栏阅读顺序、跨页表格等。官方特性里明确写到它能去除页眉页脚/页码等干扰项、按人类阅读顺序输出文本、保留标题段落列表结构、公式转 LaTeX、表格转 HTML，并支持扫描件/乱码 PDF 自动启用 OCR。([GitHub](https://github.com/opendatalab/MinerU))

### 3.2. 它主要解决什么问题？

在 RAG 或知识库场景里，最常见的问题是：PDF 看起来清楚，但抽出来的文本乱序、表格丢结构、公式乱码、页眉页脚污染正文、双栏论文顺序错乱。MinerU 的核心价值就是把这些“视觉文档”变成可检索、可喂给模型、可二次处理的结构化内容。

论文介绍里把文档抽取方法分为 OCR、库解析、多模块解析、端到端多模态模型等路线；MinerU 早期采用的是多模块文档解析思路，结合 PDF-Extract-Kit 的布局检测、OCR、公式识别、表格识别等模型，并通过预处理/后处理规则提升最终结果质量。([ar5iv.labs.arxiv.org](https://ar5iv.labs.arxiv.org/html/2409.18839))

### 3.3. 核心能力

MinerU 的能力大致可以分成几类：

**输入格式**：支持 PDF、图片、DOCX、PPTX、XLSX。较新的版本已经把 Office 文档纳入原生解析范围，不再只是 PDF 工具。([GitHub](https://github.com/opendatalab/MinerU))

**版面理解**：能处理单栏、多栏、复杂布局，按人类阅读顺序输出；同时去除页眉、页脚、脚注、页码等干扰信息，改善语义连贯性。([GitHub](https://github.com/opendatalab/MinerU))

**结构化元素抽取**：支持提取图片、图片说明、表格、表格标题、脚注；公式可转 LaTeX，表格可转 HTML。([GitHub](https://github.com/opendatalab/MinerU))

**OCR 与多语言**：能检测扫描 PDF 和乱码 PDF，并启用 OCR；官方文档称 OCR 支持 109 种语言的检测和识别。([GitHub](https://github.com/opendatalab/MinerU))

**输出格式**：支持 Markdown、按阅读顺序排序的 JSON、富中间格式，以及布局可视化/Span 可视化结果，便于质量检查和二次开发。([GitHub](https://github.com/opendatalab/MinerU))

### 3.4. 大致工作流程

从论文描述看，MinerU 的 PDF 处理流程可以概括为四步：先做文档预处理，识别是否可解析、是否扫描件、语言、页面尺寸等；然后做内容解析，包括布局检测、公式检测、OCR、公式识别、表格识别；接着做后处理，把无效区域去掉，并根据位置信息拼接、排序；最后转换成 Markdown 或 JSON 等用户需要的格式。([ar5iv](https://ar5iv.labs.arxiv.org/html/2409.18839))

新版 MinerU 还引入了 VLM / Hybrid 路线。MinerU2.5 论文称它是 1.2B 参数的文档解析视觉语言模型，采用“粗到细”的两阶段策略：先在降采样图像上做全局布局分析，再在原始分辨率裁剪区域上做局部内容识别，以兼顾效率和高分辨率细节。([arxiv.org](https://arxiv.org/abs/2509.22186))

### 3.5. 后端模式怎么理解？

官方部署表里主要有几类后端：

| 后端 | 适合场景 | 特点 |
| --- | --- | --- |
| `pipeline` | 稳定、批量、资源有限、本地 CPU/GPU | 官方描述为快、稳定、无幻觉，可在 CPU 或 GPU 上运行。([GitHub](https://github.com/opendatalab/MinerU)) |
| `vlm-engine` | 更追求复杂文档解析质量 | 高精度，支持 vLLM / LMDeploy / mlx 生态。([GitHub](https://github.com/opendatalab/MinerU)) |
| `hybrid-engine` | 兼顾原生文本抽取与 VLM 能力 | 官方描述为高精度、原生文本提取、低幻觉。([GitHub](https://github.com/opendatalab/MinerU)) |
| `*-http-client` | 远程推理 / 多机部署 | 可连接 OpenAI-compatible 服务；`vlm-http-client` 是轻量远程客户端，不要求本地 torch。([OpenDataLab](https://opendatalab.github.io/MinerU/usage/quick_usage/)) |

简单理解：  
**pipeline** 更像传统“布局检测 + OCR + 公式/表格模型 + 规则后处理”的工程化流水线；**vlm-engine** 更偏多模态模型直接理解文档；**hybrid-engine** 则试图结合两者优势。

### 3.6. 安装与基本使用

官方推荐可以用 `uv` 安装完整功能包：([GitHub](https://github.com/opendatalab/MinerU))

```bash
pip install --upgrade pip
pip install uv
uv pip install -U "mineru[all]"
```

最简单的命令行解析方式是：([GitHub](https://github.com/opendatalab/MinerU))

```bash
mineru -p <input_path> -o <output_path>
```

如果机器没有满足 GPU 加速条件，可以指定 `pipeline` 后端在纯 CPU 环境运行：([GitHub](https://github.com/opendatalab/MinerU))

```bash
mineru -p <input_path> -o <output_path> -b pipeline
```

如果 Hugging Face 访问不方便，官方文档支持通过环境变量切换模型源到 ModelScope：([OpenDataLab](https://opendatalab.github.io/MinerU/usage/quick_usage/))

```bash
export MINERU_MODEL_SOURCE=modelscope
```

它也支持服务化部署。比如启动 FastAPI：([OpenDataLab](https://opendatalab.github.io/MinerU/usage/quick_usage/))

```bash
mineru-api --host 0.0.0.0 --port 8000
```

启动 Gradio WebUI：([OpenDataLab](https://opendatalab.github.io/MinerU/usage/quick_usage/))

```bash
mineru-gradio --server-name 0.0.0.0 --server-port 7860
```

多服务/多 GPU 场景可以用 `mineru-router` 做统一入口和任务路由。官方文档说明它暴露与 `mineru-api` 相同的一组接口，并支持聚合多个上游服务或自动启动本地 GPU worker。([OpenDataLab](https://opendatalab.github.io/MinerU/usage/quick_usage/))

### 3.7. 输出文件长什么样？

MinerU 不只输出一个 `.md` 文件。官方输出文档说明，执行 `mineru` 后会生成主 Markdown 以及用于调试、质检、二次开发的辅助文件。典型包括：

- `*.md`：适合直接用于 RAG、阅读、知识库入库。
- `*_content_list.json` / `*_content_list_v2.json`：按阅读顺序排列的扁平内容块，适合程序后处理。
- `*_middle.json`：更完整的中间结构，包含页面、块、行、span、bbox 等信息，适合二次开发。
- `*_layout.pdf`：布局分析可视化，用于检查版面识别是否正确。
- `*_span.pdf`：文本 span 可视化，主要用于 pipeline 后端的质量排查。([OpenDataLab](https://opendatalab.github.io/MinerU/reference/output_files/))

### 3.8. 适合哪些场景？

MinerU 很适合这些任务：

**RAG / 知识库预处理**：把大量 PDF、Word、PPT、Excel 转成 Markdown/JSON，再做切分、向量化、检索。

**论文和技术文档解析**：尤其是含公式、表格、双栏布局、图注的论文，普通 OCR 或 PDF 文本抽取很容易出错。

**企业文档自动化**：合同、报告、说明书、财报、扫描件等批量解析。

**数据生产与清洗**：为大模型训练、评测、知识抽取准备结构化语料。

**私有化部署**：官方强调支持本地部署，并提供 CLI、FastAPI、Gradio WebUI、Docker、Router 等多种方式。([GitHub](https://github.com/opendatalab/MinerU))

### 3.9. 项目活跃度与版本现状

截至我查看时，GitHub 页面显示该仓库约有 **68.4k stars、5.8k forks**，最新版 release 是 **mineru-3.4.0，发布于 2026 年 6 月 18 日**。3.4 版本重点升级了 pipeline 后端 OCR 能力，OCR 模型升级到 PP-OCRv6，并宣称在 OmniDocBench v1.6 上提升 OCR 准确率、优化 OCR 推理与处理流程。([GitHub](https://github.com/opendatalab/MinerU))

### 3.10. 注意点与限制

第一，文档解析本身很难。官方 Quick Start 也提醒，在复杂布局、扫描页、手写内容等场景中，解析结果可能不符合预期，并建议先用在线 demo 评估效果，再选择部署方式。([GitHub](https://github.com/opendatalab/MinerU))

第二，本地部署对环境和资源有要求。官方表格列出 Python 版本为 3.10–3.13，并提示不同后端对 CPU/GPU、显存、内存、磁盘空间有不同要求；例如完整本地能力通常需要较大的模型和依赖环境。([GitHub](https://github.com/opendatalab/MinerU))

第三，许可证不是纯 Apache 2.0。MinerU 使用“基于 Apache 2.0 并附加条件”的 MinerU Open Source License；商业使用通常允许，但如果合并口径月活超过 1 亿或月收入超过 2000 万美元，需要单独商业许可；如果基于 MinerU 向第三方提供在线服务，还需要显著标明使用了 MinerU。([GitHub](https://github.com/opendatalab/MinerU/blob/master/LICENSE.md))

### 3.11. 总结

一句话说：**MinerU 是一个面向 LLM/RAG 的高精度文档解析基础设施**。它的优势不在于“能 OCR”，而在于能把复杂文档里的文本、版面、公式、表格、图片等内容尽量还原成有结构、可检索、可二次开发的 Markdown/JSON。对于搭建知识库、解析论文、处理企业文档、做数据生产，它比普通 PDF 文本抽取或单纯 OCR 更完整；但对于极复杂扫描件、手写件或低资源机器，本地部署和效果评估都需要提前测试。

## 4. 引用

- [MinerU github][1]
- [MinerU 官网][2]

[1]: https://github.com/opendatalab/MinerU
[2]: https://mineru.net/
