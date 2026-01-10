# Makepad 的 Claude Skills

[English](./README.md) | [中文](./README.zh-CN.md) | [日本語](./README.ja.md)

[![Version](https://img.shields.io/badge/version-1.10.0-blue.svg)](./skills/.claude-plugin/plugin.json)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](./LICENSE)

用于在 Rust 中使用 [Makepad](https://github.com/makepad/makepad) 框架构建跨平台 UI 应用的 Claude Code Skills。

## 关于 Makepad

[Makepad](https://github.com/makepad/makepad) 是一个用 Rust 编写的新一代 UI 框架，能够构建高性能的跨平台应用。主要特性包括：

- **跨平台**：单一代码库支持桌面端（macOS、Windows、Linux）、移动端（Android、iOS）和 Web（WebAssembly）
- **GPU 加速**：基于自定义着色器的渲染，使用 SDF（有向距离场）绘制
- **实时设计**：可热重载的 `live_design!` DSL，实现快速 UI 开发
- **高性能**：原生编译，无虚拟 DOM，极低的运行时开销

## 关于 Robius

[Project Robius](https://github.com/project-robius) 是一个开源项目，致力于用 Rust 构建功能完整的应用开发框架。使用 Makepad 构建的生产级应用包括：

- **[Robrix](https://github.com/project-robius/robrix)** - Matrix 聊天客户端，展示了实时消息、端到端加密和复杂 UI 模式
- **[Moly](https://github.com/moxin-org/moly)** - AI 模型管理器，展示了数据密集型界面和异步操作

这些 Skills 提取自 Robrix 和 Moly 中使用的模式。

## 安装

将 `skills` 文件夹复制到你的 Makepad 项目的 `.claude/skills` 目录：

```bash
# 克隆此仓库
git clone https://github.com/project-robius/makepad-skills.git

# 复制到你的项目
cp -r makepad-skills/skills your-project/.claude/skills
```

安装后的项目结构：

```
your-project/
├── .claude/
│   └── skills/
│       ├── .claude-plugin/
│       │   └── plugin.json
│       ├── makepad-init/
│       ├── makepad-fundamentals/
│       └── ... (其他 skills)
├── src/
└── Cargo.toml
```

更多详情请参阅 [Claude Code Skills 官方文档](https://docs.anthropic.com/en/docs/claude-code/skills)。

## Skills 概览

### 入门

| Skill | 描述 | 使用场景 |
|-------|------|----------|
| [makepad-init](./skills/makepad-init/SKILL.md) | 项目脚手架 | "创建一个新的 Makepad 应用" |
| [makepad-project-structure](./skills/makepad-project-structure/SKILL.md) | 目录组织最佳实践 | "我应该如何组织 Makepad 项目？" |

### 核心开发

| Skill | 描述 | 使用场景 |
|-------|------|----------|
| [makepad-fundamentals](./skills/makepad-fundamentals/SKILL.md) | `live_design!` 宏、组件、事件、定时器 | "如何创建按钮？"、"处理点击事件" |
| [makepad-rust](./skills/makepad-rust/SKILL.md) | 所有权、派生宏、async/tokio、状态管理 | "借用检查器错误"、"Makepad 中如何做异步？" |
| [makepad-shaders](./skills/makepad-shaders/SKILL.md) | SDF 绘制、自定义着色器、视觉效果 | "创建渐变背景"、"实现发光动画效果" |
| [makepad-patterns](./skills/makepad-patterns/SKILL.md) | 模态框、列表、导航、主题 | "添加模态对话框"、"实现无限滚动" |
| [makepad-adaptive-layout](./skills/makepad-adaptive-layout/SKILL.md) | 响应式布局、AdaptiveView、StackNavigation | "同时支持桌面端和移动端" |

### 部署

| Skill | 描述 | 使用场景 |
|-------|------|----------|
| [makepad-packaging](./skills/makepad-packaging/SKILL.md) | 构建桌面端、Android、iOS、WebAssembly | "构建 Android APK"、"部署到 Web" |

### 质量与调试

| Skill | 描述 | 使用场景 |
|-------|------|----------|
| [makepad-troubleshooting](./skills/makepad-troubleshooting/SKILL.md) | 常见错误及修复 | "Apply error: no matching field"、"UI 不更新" |
| [makepad-code-quality](./skills/makepad-code-quality/SKILL.md) | Makepad 感知的代码重构 | "简化这段代码"（知道哪些不能简化） |

### 自我改进

| Skill | 描述 | 使用场景 |
|-------|------|----------|
| [makepad-evolution](./skills/makepad-evolution/SKILL.md) | 在开发过程中捕获学习成果 | 发现新模式时自动触发 |

## 使用示例

### 创建新项目
```
用户: 创建一个名为 "my-app" 的 Makepad 应用，包含一个计数器按钮
Claude: [使用 makepad-init 搭建项目，使用 makepad-fundamentals 实现按钮/计数器]
```

### 添加异步数据获取
```
用户: 从 API 获取用户数据，不要阻塞 UI
Claude: [使用 makepad-rust 的 tokio 架构，使用 makepad-patterns 的加载状态]
```

### 构建移动端
```
用户: 为 Android 构建我的应用
Claude: [使用 makepad-packaging 生成 APK]
```

### 修复编译错误
```
用户: 遇到 "no matching field: font" 错误
Claude: [使用 makepad-troubleshooting 识别正确的 text_style 语法]
```

## 你可以构建什么

使用这些 Skills，Claude 可以帮助你：

- 使用正确的结构初始化新的 Makepad 项目
- 使用 `live_design!` DSL 创建自定义组件
- 处理事件和用户交互
- 编写 GPU 着色器实现视觉效果
- 实现流畅的动画
- 使用 async/tokio 管理应用状态
- 构建响应式的桌面端/移动端布局
- 为所有平台打包应用

## 基于这些 Skills 构建的项目

使用 makepad-skills 和 Claude Code 创建的真实项目：

| 项目 | 描述 | 耗时 |
|------|------|------|
| [makepad-skills-demo](https://github.com/ZhangHanDong/makepad-skills-demo) | 汇率转换应用示例 | 约 20 分钟 |
| [makepad-component](https://github.com/ZhangHanDong/makepad-component) | 可复用的 Makepad 组件库 | - |

### makepad-skills-demo 截图

<p align="center">
  <img src="./assets/skill-app-demo.jpg" width="60%" alt="汇率转换应用" />
</p>

### makepad-component 截图

<p align="center">
  <img src="./assets/mc1.png" width="45%" alt="组件 1" />
  <img src="./assets/mc2.png" width="45%" alt="组件 2" />
</p>
<p align="center">
  <img src="./assets/mc3.png" width="45%" alt="组件 3" />
  <img src="./assets/mc4.png" width="45%" alt="组件 4" />
</p>

## 资源

- [Makepad 仓库](https://github.com/makepad/makepad)
- [Makepad 示例](https://github.com/makepad/makepad/tree/main/examples)
- [Project Robius](https://github.com/project-robius)
- [Robrix](https://github.com/project-robius/robrix)
- [Moly](https://github.com/moxin-org/moly)

## 许可证

MIT
