# ProjectMemo — 项目记忆快照

> 🧠 AI 编码的"外置大脑"：一次扫描，永久复用，不再重复消耗 Token。

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Skill-blue)](https://claude.ai/code)

## 💡 解决什么问题？

AI 编码最大的痛点：**每次新开会话都要重读整个项目**。

同一份 `src/utils/helper.ts` 被不同会话分别读了 10 遍，每次都消耗 Token 去理解同一件事。模块关系、文件用途、组件依赖——这些信息每次都要从头推导。

**ProjectMemo 就是 AI 的"项目外置记忆"**：AI 浏览项目后，把关键信息持久化到 `ProjectMemo.md`，下次直接读这份记忆，秒懂项目结构。

```
传统方式：新会话 → 重读项目 → 理解结构 → 开始工作（浪费 Token）
ProjectMemo：新会话 → 读 ProjectMemo.md → 秒懂结构 → 开始工作（节省 Token）
```

## ✨ 核心能力

| 能力 | 说明 |
|------|------|
| 🚀 **首次生成** | AI 浏览项目后自动生成结构化 ProjectMemo.md |
| 🔄 **增量更新** | 文件变更时只更新变动部分，不重写整个文档 |
| 🔍 **变更检测** | 基于 Git 自动检测文件新增/修改/删除/重命名 |
| 📋 **智能跳过** | 注释、格式化等微调不触发更新，避免无效刷新 |
| 🧩 **模块关系** | 自动梳理模块间依赖关系，层级一目了然 |
| 💾 **跨会话持久化** | 关机重启、新开会话都不会丢失项目记忆 |

## 📦 安装

### 方式一：通过 Skill 文件安装

1. 下载 [project-memo.skill](https://github.com/lhao17202-hue/ProjectMemo/releases/latest) 文件
2. 在 Claude Code 中拖入 `.skill` 文件即可安装

### 方式二：手动安装

```bash
# 克隆到 Claude Code 的 skills 目录
git clone https://github.com/lhao17202-hue/ProjectMemo.git ~/.claude/skills/project-memo
```

### 方式三：在 Claude Code 中搜索安装

在 Claude Code 中输入：
```
/skill-install project-memo
```

## 🎯 使用方式

安装后，Skill 会根据你的对话自动触发。以下场景都会激活 ProjectMemo：

| 你对 AI 说 | 触发的行为 |
|-----------|-----------|
| "帮我梳理一下项目结构" | 扫描项目 → 生成 ProjectMemo.md |
| "这个项目有哪些模块？" | 读 ProjectMemo.md → 直接回答 |
| "我改了 src/utils/helper.ts，更新一下记忆" | Git diff 检测变更 → 增量更新 |
| "我刚接手这个项目，帮我快速了解" | 生成 ProjectMemo.md → 展示关键信息 |
| 任何涉及项目结构的对话 | 优先读取记忆，减少重复扫描 |

## 📄 ProjectMemo.md 长什么样？

生成的记忆文档结构清晰，人机共读：

```markdown
# ProjectMemo — MyApp

> 📅 最后更新: 2026-07-16 14:30 | 📄 跟踪文件: 23 个 | 🔖 Git: abc1234

## 📁 项目概览
- 项目类型、技术栈、入口文件、构建命令

## 📁 目录结构
- 树形目录，标注各目录职责

## 📄 文件索引
- 每个核心文件的用途、导出、依赖、被引用情况

## 🔗 模块关系
- 模块间的依赖层级和调用关系

## 📝 变更记录
- 时间线式的变更日志
```

## 🏗️ 设计原则

- **轻量优先**：不追求详尽文档，只记录"下次会话最需要的"关键信息
- **增量优先**：只更新变化的部分，不重写整个文档
- **可读优先**：人类和 AI 都容易阅读的 Markdown 格式
- **按需触发**：用户浏览项目时自动判断是否需要生成或更新
- **零配置**：无需安装依赖、无需配置文件、无需 Hook

## 🔧 项目结构

```
project-memo/
├── SKILL.md          # Skill 定义（核心）
├── README.md         # 项目说明（本文件）
├── LICENSE           # MIT 许可证
└── evals/            # 测试用例
    └── evals.json
```

就这些。没有脚本，没有复杂配置。

## 🤝 贡献

欢迎提 Issue 和 PR！

如果你有好的想法（比如支持多语言、支持更多项目类型、优化检测策略），请通过以下方式参与：

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/amazing-idea`)
3. 提交更改 (`git commit -m 'feat: add amazing idea'`)
4. 推送到分支 (`git push origin feature/amazing-idea`)
5. 创建 Pull Request

## 📝 许可证

MIT © 2026 [ProjectMemo Contributors](https://github.com/lhao17202-hue/ProjectMemo/graphs/contributors)

---

**ProjectMemo** — 让 AI 不再失忆，让每一轮对话都站在上次的肩膀上。
