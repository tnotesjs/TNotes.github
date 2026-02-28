# [0004. OAuth](https://github.com/tnotesjs/TNotes.github/tree/main/notes/0004.%20OAuth)

<!-- region:toc -->

- [1. 🎯 本节内容](#1--本节内容)
- [2. 🫧 评价](#2--评价)
- [3. 💻 做法 1：在 Settings 中的 Applications 面板中撤销应用的授权（推荐）](#3--做法-1在-settings-中的-applications-面板中撤销应用的授权推荐)
- [4. 💻 做法 2：使用 API 撤销令牌](#4--做法-2使用-api-撤销令牌)

<!-- endregion:toc -->

## 1. 🎯 本节内容

- todo

## 2. 🫧 评价

::: warning

以下内容来自原 TNotes.git-notes 的 `0017. 如何取消 github 上某个 OAuth 应用的访问权限` 笔记。

:::

- 要取消 GitHub 上某个 OAuth 应用的访问权限，可通过网页操作（直观）或 GitHub 提供的开发者接口（如果需要批处理的话，不过大概率用不到）来实现。
- 做法 2 中记录的是 AI 提供的方案，未实际测试过。

## 3. 💻 做法 1：在 Settings 中的 Applications 面板中撤销应用的授权（推荐）

- 登录 GitHub，点击右上角头像 → **Settings**（设置）。
  - 1️⃣ 左侧菜单选择 **Applications**
  - 2️⃣ 选择 **Authorized OAuth Apps**（已授权的 OAuth 应用）

::: swiper

![1](https://cdn.jsdelivr.net/gh/tnotesjs/imgs@main/2025-07-26-00-20-53.png)

![2](https://cdn.jsdelivr.net/gh/tnotesjs/imgs@main/2025-07-26-00-31-26.png)

:::

- 找到目标应用，点击 **Revoke**（撤销）并确认。
- 取消后应用将立即失去访问权限，且无法再获取你的私有数据。

## 4. 💻 做法 2：使用 API 撤销令牌

- 若需以编程方式撤销单个访问令牌（如用户退出应用时），可调用 GitHub API：

```bash
curl -X DELETE \
  -H "Accept: application/vnd.github.v3+json" \
  -u "CLIENT_ID:CLIENT_SECRET" \
  https://api.github.com/applications/CLIENT_ID/token \
  -d '{"access_token":"ACCESS_TOKEN"}'
```

- **参数说明**：
  - `CLIENT_ID`/`CLIENT_SECRET`：OAuth 应用的凭证。
  - `ACCESS_TOKEN`：需撤销的令牌。
- **注意**：此操作仅使当前令牌失效，不影响其他授权。
