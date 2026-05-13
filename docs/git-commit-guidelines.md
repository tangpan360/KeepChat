# Git Commit Guidelines

## 目标
本项目采用基于 Conventional Commits 的提交规范，并在前缀中加入 emoji，提高提交历史的可读性与可扫描性。

规范目标：
- 让提交历史更清晰
- 让每次提交表达单一意图
- 便于后续生成变更日志
- 便于代码审查、问题定位与版本回溯

## 推荐格式
```text
emoji type(scope): subject
```

说明：
- `emoji`：推荐使用，用于快速表达变更类型
- `type`：必填，表示提交类别
- `scope`：可选，表示影响范围或模块
- `subject`：必填，简洁描述本次提交

示例：
```text
✨ feat(chat): add image upload support
🐛 fix(sidebar): restore input focus after quote action
📝 docs(architecture): add system layering notes
♻️ refactor(api): split conversation service
```

## 常用提交类型
### 核心类型
- `✨ feat`：新功能
- `🐛 fix`：Bug 修复
- `📝 docs`：文档变更
- `💄 style`：样式或 UI 调整，不影响业务逻辑
- `♻️ refactor`：重构，不新增功能也不修复 Bug
- `⚡️ perf`：性能优化
- `✅ test`：测试相关
- `🔧 chore`：杂项、配置、脚手架、非功能性改动

### 可选补充类型
- `📦 deps`：依赖升级、替换或移除
- `👷 ci`：CI/CD、工作流、自动化流程
- `🔒 security`：安全修复
- `🔥 remove`：删除代码、废弃功能或清理历史逻辑
- `🗃️ db`：数据库结构、迁移、索引相关

## scope 书写建议
`scope` 用于标识本次提交主要影响的模块，建议保持简短、稳定、可复用。

推荐 scope 示例：
- `sidebar`
- `chat`
- `api`
- `auth`
- `docs`
- `rag`
- `pdf`
- `editor`
- `parser`
- `config`

示例：
```text
✨ feat(sidebar): add quick action buttons
🐛 fix(chat): handle empty assistant response
♻️ refactor(rag): simplify retrieval pipeline
```

如果本次变更影响范围较广，或没有明显模块，可以省略 scope：
```text
🔧 chore: update editor settings
📝 docs: add commit guidelines
```

## subject 书写规则
`subject` 应尽量简洁明确，直接说明本次提交做了什么。

建议：
- 使用短句
- 尽量使用动词开头
- 聚焦本次改动，不写泛泛描述
- 不要以句号结尾
- 中英文任选，但团队内应保持一致

推荐写法：
```text
✨ feat(chat): add streaming response support
🐛 fix(sidebar): prevent duplicate send on enter
📝 docs(v1): define current feature scope
```

不推荐写法：
```text
✨ feat: update project
🐛 fix: fix bug
🔧 chore: misc changes
```

## 提交粒度要求
一个 commit 应尽量只做一件事。

好的提交：
```text
✨ feat(chat): add image upload support
🐛 fix(api): validate missing attachment ids
📝 docs(commit): add team commit guidelines
```

不好的提交：
```text
✨ feat: add image upload and update docs and fix sidebar focus
```

如果一个需求包含多个独立改动，优先拆成多个 commit。

## Breaking Change 规则
如果本次提交包含破坏性变更，可在 `type` 后添加 `!`：

```text
🔥 refactor(api)!: redesign stream response format
```

必要时可在正文中补充说明：

```text
✨ feat(auth)!: replace session auth with token auth

BREAKING CHANGE: previous session-based login is no longer supported
```

适用场景：
- API 不兼容
- 配置方式变化
- 数据结构重大调整
- 删除旧功能

## 提交正文建议
当改动较复杂时，建议为 commit 增加正文，说明背景和主要变化。

示例：
```text
✨ feat(rag): add multi-page context support

- support multiple selected pages in one conversation
- store page metadata separately from message body
- prepare for future PDF retrieval
```

正文适合说明：
- 为什么这样改
- 改动的主要思路
- 当前限制或后续计划

## 本项目推荐类型与 scope
考虑到本项目的技术方向，优先使用以下类型：
- `✨ feat`
- `🐛 fix`
- `📝 docs`
- `♻️ refactor`
- `⚡️ perf`
- `✅ test`
- `🔧 chore`
- `📦 deps`
- `👷 ci`
- `🔒 security`

推荐 scope：
- `sidebar`
- `chat`
- `api`
- `auth`
- `docs`
- `rag`
- `pdf`
- `editor`
- `parser`
- `config`

## 推荐示例
```text
✨ feat(sidebar): add current page context action
✨ feat(chat): support image attachments
🐛 fix(sidebar): keep input focused after quote action
🐛 fix(api): return clear error for expired token
📝 docs: add architecture principles
📝 docs(commit): define git commit rules
♻️ refactor(api): extract ai orchestration module
⚡️ perf(rag): reduce duplicate retrieval requests
✅ test(chat): add stream response parsing tests
🔧 chore: update repository settings
📦 deps: upgrade langchain packages
👷 ci: add markdown lint workflow
```

## 最低执行标准
如果后续希望逐步收紧规范，建议至少先保证以下几点：
- 每次提交必须有明确 `type`
- 推荐使用 `scope`
- 推荐使用 emoji
- `subject` 必须清晰、具体
- 一个 commit 尽量只表达一件事

本项目推荐的最终格式为：
```text
emoji type(scope): subject
```
