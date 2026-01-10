# Claude Skills for Makepad

[English](./README.md) | [中文](./README.zh-CN.md) | [日本語](./README.ja.md)

[![Version](https://img.shields.io/badge/version-1.10.0-blue.svg)](./skills/.claude-plugin/plugin.json)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](./LICENSE)

Claude Code skills for building cross-platform UI applications with the [Makepad](https://github.com/makepad/makepad) framework in Rust.

## About Makepad

[Makepad](https://github.com/makepad/makepad) is a next-generation UI framework written in Rust that enables building high-performance, cross-platform applications. Key features include:

- **Cross-Platform**: Single codebase for Desktop (macOS, Windows, Linux), Mobile (Android, iOS), and Web (WebAssembly)
- **GPU-Accelerated**: Custom shader-based rendering with SDF (Signed Distance Field) drawing
- **Live Design**: Hot-reloadable `live_design!` DSL for rapid UI development
- **High Performance**: Native compilation, no virtual DOM, minimal runtime overhead

## About Robius

[Project Robius](https://github.com/project-robius) is an open-source initiative to build a full-featured application development framework in Rust. Production applications built with Makepad include:

- **[Robrix](https://github.com/project-robius/robrix)** - A Matrix chat client showcasing real-time messaging, E2E encryption, and complex UI patterns
- **[Moly](https://github.com/moxin-org/moly)** - An AI model manager demonstrating data-heavy interfaces and async operations

These skills are extracted from patterns used in Robrix and Moly.

## Installation

Copy the `skills` folder to `.claude/skills` in your Makepad project:

```bash
# Clone this repo
git clone https://github.com/project-robius/makepad-skills.git

# Copy to your project
cp -r makepad-skills/skills your-project/.claude/skills
```

Your project structure should look like:

```
your-project/
├── .claude/
│   └── skills/
│       ├── .claude-plugin/
│       │   └── plugin.json
│       ├── makepad-init/
│       ├── makepad-fundamentals/
│       └── ... (other skills)
├── src/
└── Cargo.toml
```

See [Claude Code Skills documentation](https://docs.anthropic.com/en/docs/claude-code/skills) for more details.

## Skills Overview

### Getting Started

| Skill | Description | When to Use |
|-------|-------------|-------------|
| [makepad-init](./skills/makepad-init/SKILL.md) | Project scaffolding | "Create a new Makepad app" |
| [makepad-project-structure](./skills/makepad-project-structure/SKILL.md) | Directory organization best practices | "How should I organize my Makepad project?" |

### Core Development

| Skill | Description | When to Use |
|-------|-------------|-------------|
| [makepad-fundamentals](./skills/makepad-fundamentals/SKILL.md) | `live_design!` macro, widgets, events, timers | "How do I create a button?", "Handle click events" |
| [makepad-rust](./skills/makepad-rust/SKILL.md) | Ownership, derives, async/tokio, state management | "Borrow checker error", "How to do async in Makepad?" |
| [makepad-shaders](./skills/makepad-shaders/SKILL.md) | SDF drawing, custom shaders, visual effects | "Create a gradient background", "Animate a glow effect" |
| [makepad-patterns](./skills/makepad-patterns/SKILL.md) | Modals, lists, navigation, theming | "Add a modal dialog", "Implement infinite scroll" |
| [makepad-adaptive-layout](./skills/makepad-adaptive-layout/SKILL.md) | Responsive layouts, AdaptiveView, StackNavigation | "Support both desktop and mobile" |

### Deployment

| Skill | Description | When to Use |
|-------|-------------|-------------|
| [makepad-packaging](./skills/makepad-packaging/SKILL.md) | Build for desktop, Android, iOS, WebAssembly | "Build APK for Android", "Deploy to web" |

### Quality & Debugging

| Skill | Description | When to Use |
|-------|-------------|-------------|
| [makepad-troubleshooting](./skills/makepad-troubleshooting/SKILL.md) | Common errors and fixes | "Apply error: no matching field", "UI not updating" |
| [makepad-code-quality](./skills/makepad-code-quality/SKILL.md) | Makepad-aware refactoring | "Simplify this code" (knows what NOT to simplify) |

### Self-Improvement

| Skill | Description | When to Use |
|-------|-------------|-------------|
| [makepad-evolution](./skills/makepad-evolution/SKILL.md) | Capture learnings during development | Auto-triggered when discovering new patterns |

## Usage Examples

### Create a New Project
```
User: Create a new Makepad app called "my-app" with a counter button
Claude: [Uses makepad-init to scaffold project, makepad-fundamentals for button/counter]
```

### Add Async Data Fetching
```
User: Fetch user data from an API without blocking the UI
Claude: [Uses makepad-rust for tokio architecture, makepad-patterns for loading states]
```

### Build for Mobile
```
User: Build my app for Android
Claude: [Uses makepad-packaging for APK generation]
```

### Fix Compilation Error
```
User: Getting "no matching field: font" error
Claude: [Uses makepad-troubleshooting to identify correct text_style syntax]
```

## What You Can Build

With these skills, Claude can help you:

- Initialize new Makepad projects with proper structure
- Create custom widgets with `live_design!` DSL
- Handle events and user interactions
- Write GPU shaders for visual effects
- Implement smooth animations
- Manage application state with async/tokio
- Build responsive desktop/mobile layouts
- Package apps for all platforms

## Projects Built with These Skills

Real-world projects created using makepad-skills and Claude Code:

| Project | Description | Time |
|---------|-------------|------|
| [makepad-skills-demo](https://github.com/ZhangHanDong/makepad-skills-demo) | Currency converter app demo | ~20 min |
| [makepad-component](https://github.com/ZhangHanDong/makepad-component) | Reusable Makepad component library | - |

### makepad-skills-demo Screenshot

<p align="center">
  <img src="./assets/skill-app-demo.jpg" width="60%" alt="Currency Converter App" />
</p>

### makepad-component Screenshots

<p align="center">
  <img src="./assets/mc1.png" width="45%" alt="Component 1" />
  <img src="./assets/mc2.png" width="45%" alt="Component 2" />
</p>
<p align="center">
  <img src="./assets/mc3.png" width="45%" alt="Component 3" />
  <img src="./assets/mc4.png" width="45%" alt="Component 4" />
</p>

## Resources

- [Makepad Repository](https://github.com/makepad/makepad)
- [Makepad Examples](https://github.com/makepad/makepad/tree/main/examples)
- [Project Robius](https://github.com/project-robius)
- [Robrix](https://github.com/project-robius/robrix)
- [Moly](https://github.com/moxin-org/moly)

## License

MIT
