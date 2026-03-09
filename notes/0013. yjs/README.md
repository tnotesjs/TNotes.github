# [0013. yjs](https://github.com/tnotesjs/TNotes.github/tree/main/notes/0013.%20yjs)

<!-- region:toc -->

- [1. 🎯 本节内容](#1--本节内容)
- [2. 🫧 评价](#2--评价)
- [3. 🤔 Yjs 是什么？](#3--yjs-是什么)
- [4. 🤔 CRDT 算法是什么？](#4--crdt-算法是什么)
- [5. 🤔 CRDT 的核心原理是？](#5--crdt-的核心原理是)
- [6. 🤔 Yjs 都有哪些常见的使用场景？](#6--yjs-都有哪些常见的使用场景)
- [7. 🤔 为什么叫 YJS，其中的 Y 是什么意思？](#7--为什么叫-yjs其中的-y-是什么意思)
- [8. 🔗 引用](#8--引用)

<!-- endregion:toc -->

## 1. 🎯 本节内容

- yjs

## 2. 🫧 评价

Yjs 是一个用于构建实时协作应用的开源 JavaScript 库，常用与在线文档多人协作的场景。

## 3. 🤔 Yjs 是什么？

Yjs 是一个用于构建实时协作应用的开源 JavaScript 库。它通过 CRDT 算法，使多人能同时编辑同一份数据（如文本、数组），并自动合并修改，无需处理冲突。

核心亮点：

- 多种共享数据类型：提供类似 Map、Array 的数据结构，并内置 `Y.Text` 专门处理富文本。
- 网络无关：核心不绑定传输层，可用 WebSocket、WebRTC 甚至离线存储。
- 模块化设计：提供灵活的 API 和插件系统，方便集成到各种前端框架中。
- 跨平台：支持浏览器和 Node.js 环境。
- 生态丰富：完美集成 Quill、Monaco、ProseMirror 等主流编辑器，并有现成的后端与数据库方案。
- 高性能：在 CRDT 实现中表现优异，处理大型文档和多人协作依然流畅。

## 4. 🤔 CRDT 算法是什么？

CRDT（无冲突复制数据类型，Conflict-Free Replicated Data Type）是一种专门用于在分布式系统中实现数据最终一致性的算法。

简单来说，它允许网络中的多个副本独立、并发地更新数据，并且不需要中央服务器进行协调。算法本身能保证所有副本最终会达到一致的状态，且绝对不会发生数据冲突或丢失。

## 5. 🤔 CRDT 的核心原理是？

- CRDT 的核心设计哲学是：让操作本身变得可交换（Commutative）。它确保无论操作以什么顺序到达，最终计算出的结果都是一样的。
- CRDT 的原理就是：让数据结构的每一次变更都成为一个“原子事件”，这些事件不管以什么顺序到达，都能通过数学法则（交换律）和唯一标识，收敛出完全相同的结果。

具体通过以下两个关键机制实现：

1. 仅允许满足交换律的操作 CRDT 数据结构的设计确保所有并发修改操作在数学上是可以交换顺序的。
   - 比如：一个共享计数器，A 加 1，B 加 1。无论服务器先收到 A 的指令还是 B 的指令，最终结果都是加 2。
   - 对应到 Yjs：在文本编辑中，插入字符“A”和插入字符“B”这两个操作，即使在不同位置，最终也能被正确合并，而不会相互覆盖。
2. 唯一标识与偏序（以 Yjs 使用的位置图谱 CRDT 为例） 为了处理复杂的文本插入（不仅仅是计数器），CRDT 需要解决“谁在谁前面”的问题。
   - 唯一 ID：每个操作（如插入一个字符）都被赋予一个全局唯一的 ID，通常由`[节点ID, 逻辑时间戳]`组成。
   - 因果关系：通过 ID 记录操作的先后顺序和位置关系。
   - 原理：当两个用户在同一个位置插入不同内容时（比如一个人插入“AB”，另一个人插入“CD”），CRDT 会根据它们的唯一 ID 定义一个确定的排序规则（比如节点 ID 小的排在左边）。最终，所有副本都会按照这个确定性规则排列出相同的结果（比如变成“ABCD”或“CDAB”），而不是随机覆盖或报错。

## 6. 🤔 Yjs 都有哪些常见的使用场景？

- 在线文档协作工具（如 Google Docs 类似功能）
- 实时聊天与协同白板
- 多人游戏或协同开发工具

## 7. 🤔 为什么叫 YJS，其中的 Y 是什么意思？

关于 Yjs 中“Y”的具体含义，项目官方并没有给出明确的解释。

当你问 AI 这个问题时，它估计会根据以 Y 开头的相关词汇并集合 Yjs 的核心特性来硬猜。

```
下面 👇 是来自 Google Search 的 AI Summary，可以作为一个参考：

The "Y" in Yjs could be interpreted in several ways, potentially relating to:

- Yielding: The idea of yielding changes from different users to be merged, possibly with a focus on "yes" to the merging operation.
- Y-combinator: While not directly a Y-combinator, the concept of recursion and self-reference could be relevant to the way Yjs handles data structures.
- Merging: The core function of Yjs is to merge changes from different sources, so the "Y" could represent the merging operation.

中文：

Yjs 中的 "Y "可以有多种解释，可能与以下方面有关：

- 让渡：让渡来自不同用户的变更以进行合并的想法，可能侧重于合并操作的 "是"。
- Y-combinator：虽然不是直接的 Y-combinator，但递归和自我引用的概念可能与 Yjs 处理数据结构的方式有关。
- 合并：Yjs 的核心功能是合并来自不同来源的更改，因此 "Y "可以代表合并操作。
```

注意，上述内容只是一个 AI 的猜测，当你进一步询问其结论的来源时，它就哑口无言了。最准确的含义可能只有项目作者本人知道。

## 8. 🔗 引用

- [YJS - github][1]
- [YJS - 官方文档][2]

[1]: https://github.com/yjs/yjs
[2]: https://docs.yjs.dev/
