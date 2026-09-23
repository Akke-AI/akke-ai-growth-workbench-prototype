# AKKE 营销增长工作台 · V5 交互原型（公开预览）

> **状态：交互原型 · 演示数据 · 非生产系统。**
> 这里只放给 PM / 团队评审用的静态成品；页面里的客户、门店、数字全是演示数据，不要当成真实系统读。

公开访问：<https://akke-ai.github.io/akke-ai-growth-workbench-prototype/>

## 这个仓里有什么

| 路径 | 是什么 |
|---|---|
| `docs/index.html` · `docs/assets/` | 构建产物（GitHub Pages 的发布根）。版本号在 `<title>` / `og:title` 里 |
| `docs/demos/` | 13 段功能演示视频（mp4），页面内嵌播放 |
| `docs/video-previews/` | 演示视频的封面图 |

**没有源代码。** 完整源码在 AKKE 的私有仓里，这里是从那边构建后拷贝进来的产物。

## 怎么更新这份预览

1. 在私有源码仓构建出静态产物
2. 覆盖本仓 `docs/`（`demos/`、`video-previews/` 不随构建产出，除非要换视频否则保留）
3. push 到 `main`。GitHub Pages 配置是 **`main` 分支的 `/docs` 目录**，push 后几分钟内自动重新发布
4. 换版本时同步改三处：`docs/index.html` 的 `<title>` 与 `og:title`、仓库描述

## 与其它仓的关系

- 生产实现在 [`Akke-AI/store-workbench`](https://github.com/Akke-AI/store-workbench)：它的 UI 照搬本原型、只把假数据换成真实查询。
  那边 README「和别的仓的关系」一节写了同步方式（clone 本仓 → diff `app/prototype-*.tsx` → 手工合并）
- 全 org「哪件事归哪个仓」以 [`Akke-AI/Akke`](https://github.com/Akke-AI/Akke) 的 `docs/REPO-MAP.md` 为准

## 仓库协作与自动化

- 合并方式：本仓未开原生 auto-merge、没有 CI workflow，也没有 pr-janitor；PR 由维护者确认后手动 squash 合并
- 分支保护：`main` 无分支保护，无 required checks
- 发布：GitHub Pages（legacy 构建，源为 `main` 分支 `/docs`），合进 `main` 即触发重新发布
- 合并后分支自动删除（仓库设置 `delete_branch_on_merge`）
- 由维护者本机每周执行 repo-hygiene，清理已合并 / 已关闭 PR 的残留分支
