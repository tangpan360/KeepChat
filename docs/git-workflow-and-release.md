# Git Workflow and Release

## 目的
本文件用于定义当前项目的 Git 分支策略与版本发布方式。

目标是保持流程简单、清晰、可执行，避免在项目早期引入过重的分支和发布管理复杂度。

## 当前采用的策略
当前项目采用：
- `main` 作为主分支
- 短期功能分支作为日常开发分支
- 关键节点通过 tag 标记版本

当前不采用：
- `develop` 长期分支
- 复杂的 Git Flow
- 提前定义 `release/*`、`hotfix/*` 等长期流程

## 分支策略
### 主分支
- `main` 为当前主分支。
- `main` 用于保存当前主线成果。
- 相对完整、可继续推进的内容最终都应合并到 `main`。

### 功能分支
当开始一个明确主题的工作时，建议从 `main` 拉出短期分支。

推荐命名：
- `feat/...`：新功能
- `fix/...`：问题修复
- `docs/...`：文档整理
- `chore/...`：杂项调整

示例：
- `feat/sidebar-chat`
- `feat/quote-tray`
- `feat/custom-actions`
- `fix/readme-encoding`
- `docs/feature-structure`

## 当前阶段的工作方式
### 小改动
如果只是极小范围的文档修正或微小调整，可以直接在当前分支完成。

### 明确主题的工作
如果开始的是一个相对完整的小任务，建议单独开分支，例如：
- 补一份完整文档
- 设计一个交互流程
- 实现一个独立功能

### 合并时机
当一个主题已经形成比较完整的结果时，再合并回 `main`。

不建议：
- 一个分支长期堆很多无关改动
- 多个主题混在同一个分支里开发太久

## 推荐开发流程
1. 先切回 `main`
2. 拉取最新内容
3. 基于 `main` 新建分支
4. 在分支上进行小步提交
5. 主题完成后合并回 `main`
6. 合并后删除本地分支

示例流程：
```bash
git checkout main
git pull
git checkout -b docs/feature-structure
```

开发完成后：
```bash
git checkout main
git merge docs/feature-structure
git branch -d docs/feature-structure
```

## Commit 方式
- 提交规范遵循 `docs/git-commit-guidelines.md`
- 一个 commit 尽量只表达一件事
- 大任务内部允许小步提交
- 不要求等所有东西都做完再一次性提交

## 版本策略
当前项目采用语义化版本号的简化形式：

```text
MAJOR.MINOR.PATCH
```

当前阶段建议从 `0.x.y` 开始。

含义：
- `MAJOR`：重大不兼容变化
- `MINOR`：新增一组明确功能
- `PATCH`：小修复、小调整

### 当前建议
- 早期原型与快速迭代阶段，使用 `0.x.y`
- 第一版可运行的原型可以定义为 `v0.1.0`
- 新增一组明显功能后，升级 `MINOR`
- 小问题修复后，升级 `PATCH`

示例：
- `v0.1.0`
- `v0.2.0`
- `v0.2.1`

## 发布策略
当前阶段不需要复杂的发布流程，采用：
- 主分支合并完成
- 在关键节点打 tag
- 记录简单 release note

### 适合打 tag 的时机
- 完成一个清晰阶段
- 获得一个可运行原型
- 完成一组重要功能
- 准备进入下一阶段前

示例：
```bash
git tag v0.1.0
git push origin v0.1.0
```

## Release Note 建议
每次版本发布时，不需要写很长，只需要简要记录：
- 这个版本做了什么
- 主要新增哪些能力
- 当前已知限制是什么

例如：
```text
v0.1.0
- add sidebar chat
- support image Q&A
- support quote tray
- add default quick actions
```

## 当前阶段不建议做的事
- 不提前引入 `develop`
- 不提前设计复杂 release 分支
- 不提前为个人项目套用企业级 Git Flow
- 不为了“看起来专业”而增加流程负担

## 当前项目的推荐原则
- 保持 `main` 清晰
- 用短期分支处理明确主题
- 小步提交
- 在关键节点打 tag
- 保持流程简单，可长期坚持
