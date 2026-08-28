# Rokid Prism

> Your agents, in one calm place.

[![License: MIT](https://img.shields.io/badge/License-MIT-informational.svg)](./LICENSE)

**English** · [中文](#中文)

---

## What is Prism?

Prism lets you run AI coding agents where they work best — on your desktop — and stay in control from anywhere. Keep Claude Code, Codex, Hermes, or OpenClaw running on your Mac or PC, then pick up your phone or put on your Rokid glasses to check progress, continue the conversation, answer approval requests, or start new tasks.

This GitHub organization hosts the open-source heart of that ecosystem: the **PluginBridge SDK** and the **official agent plugins** that connect Prism to local agents.

## Features

- **Full visibility** — an Agent → project → thread tree with online / working status, plus usage stats such as token spend, remaining quota, and day streaks
- **Continue conversations remotely** — send messages and attachments, and follow the full conversation stream rendered with Markdown, tool calls, and step-by-step progress
- **Stay in control** — switch models, reasoning effort, and permission modes; interrupt a running task at any time
- **Approvals & planning** — resolve permission requests, manage queued messages, run agents in plan mode, and set or pause goals
- **Timely notifications** — Web Push alerts for approval requests and task completion
- **Multilingual** — English, 简体中文, 日本語

## Two ways to use Prism

- **Prism Panel (PWA)** — open <https://prism-panel.rokid.com> in a mobile or desktop browser and add it to your home screen. Install once, manage remote tasks from anywhere.
- **Rokid Glasses AIUI** — the recommended companion for Rokid glasses. Collaborate on remote tasks hands-free, any time and anywhere, right from your glasses.

## How it works

```mermaid
flowchart LR
    M["📱 Phone / Panel"]
    G["🕶️ Rokid Glasses (AIUI)"]
    C["Prism Cloud<br>(API + Realtime)"]
    H["Prism Hub<br>(desktop app)"]
    P["Plugin"]
    A["Native agent app<br>(Claude Code, Codex, ...)"]

    M --> C
    G --> C
    C <--> H
    H <--> P
    P <--> A
```

Your devices talk to the Prism cloud, the cloud talks to the Prism Hub running on your desktop, and the Hub drives each agent through a plugin. The cloud and desktop layers ship as part of the Prism product — **this organization open-sources and maintains the plugin layer**.

## Repositories

| Repository | What it does |
| --- | --- |
| [prism-plugin-sdk](https://github.com/Rokid-Prism/prism-plugin-sdk) | The PluginBridge SDK for building plugins — published as a Go module (`github.com/Rokid-Prism/prism-plugin-sdk`), an npm package (`@rokid-prism/pluginbridge-plugin-sdk`), and a PyPI package (`rokid-pluginbridge-plugin-sdk`). Also defines the plugin manifest schema and conformance suite. |
| [prism-plugin-claude-code](https://github.com/Rokid-Prism/prism-plugin-claude-code) | Official Claude Code plugin — protocol-native, speaking ACP to a local `claude` runtime |
| [prism-plugin-codex](https://github.com/Rokid-Prism/prism-plugin-codex) | Official Codex plugin — automates Codex Desktop to browse sessions, read history, and continue threads |
| [prism-plugin-hermes](https://github.com/Rokid-Prism/prism-plugin-hermes) | Official Hermes plugin — remote sessions via the Hermes gateway |
| [prism-plugin-openclaw](https://github.com/Rokid-Prism/prism-plugin-openclaw) | Official OpenClaw plugin — protocol-native against the OpenClaw gateway |

### How plugins work

Each plugin is a small program described by a `pluginbridge-plugin.yaml` manifest. Plugins connect in one of two ways:

- **Protocol-native** — talk to the agent through its own protocol (an API, RPC, or CLI), e.g. OpenClaw's gateway or Claude Code over ACP
- **Desktop automation** — drive the agent's desktop app when no protocol is available, e.g. Codex

Plugins are distributed as GitHub Releases; the Hub discovers, installs, and updates them automatically. See each repository's README for details.

## Contributing

There are two great ways to help Prism support more agents, better:

### 1. Adapt a plugin when an agent updates

Agents move fast — a new release can change menus, UI, or behavior. If an agent you use has updated and its Prism plugin no longer keeps up, that's a perfect contribution: open an issue on the plugin's repository describing what changed, or submit a pull request adapting the plugin yourself.

### 2. Create a plugin for a new agent

Want Prism to support an agent that isn't covered yet? Create a new repository, build a plugin with the [prism-plugin-sdk](https://github.com/Rokid-Prism/prism-plugin-sdk), publish a release, and submit it to the Hub's plugin registry. Once registered, every Prism user can discover and install your plugin.

**Pull requests**: fork the repository, create a branch, and open a PR. Please follow [Conventional Commits](https://www.conventionalcommits.org) (`feat:`, `fix:`, `chore:`) as the existing history does. All public repositories here are MIT licensed, and contributions are accepted under the same license.

## License

All public repositories in this organization are released under the [MIT License](https://opensource.org/license/mit).

---

# 中文

**[English](#what-is-prism)** · **中文**

## Prism 是什么？

Prism 让 AI 编程智能体在最适合它们的地方运行——你的桌面——同时让你在任何地方都保持掌控。让 Claude Code、Codex、Hermes 或 OpenClaw 在你的 Mac 或 PC 上持续工作，然后拿起手机、或戴上 Rokid 眼镜，随时查看进度、继续对话、处理审批，或发起新任务。

本 GitHub 组织托管这个生态的开源核心：**PluginBridge SDK** 与连接 Prism 与本地智能体的**官方插件**。

## 产品功能

- **全局可见** — Agent → 项目 → 线程三层视图，在线 / 工作中状态一目了然，还有 token 用量、剩余额度、连续使用天数等用量统计
- **远程继续对话** — 发送消息与附件，完整对话流实时渲染，支持 Markdown、工具调用与逐步执行进度
- **掌控全局** — 切换模型、推理强度与权限模式，随时中断正在运行的任务
- **审批与规划** — 处理权限审批、管理排队消息、以计划模式运行智能体、设置或暂停目标
- **及时通知** — 审批请求与任务完成的 Web Push 提醒
- **多语言** — English、简体中文、日本語

## 两种使用方式

- **Prism Panel（PWA）** — 在手机或桌面浏览器打开 <https://prism-panel.rokid.com>，即可添加到主屏幕。一次安装，随处管理远程任务。
- **Rokid Glasses AIUI** — 推荐搭配 Rokid 眼镜使用。通过眼镜随时随地进行远程任务协作，解放双手。

## 工作原理

```mermaid
flowchart LR
    M["📱 Phone / Panel"]
    G["🕶️ Rokid Glasses (AIUI)"]
    C["Prism Cloud<br>(API + Realtime)"]
    H["Prism Hub<br>(desktop app)"]
    P["Plugin"]
    A["Native agent app<br>(Claude Code, Codex, ...)"]

    M --> C
    G --> C
    C <--> H
    H <--> P
    P <--> A
```

你的设备与 Prism 云端通信，云端与运行在桌面上的 Prism Hub 通信，Hub 再通过插件驱动各个智能体。云端与桌面端随 Prism 产品发布——**本组织开源并维护的是插件层**。

## 仓库结构

| 仓库 | 作用 |
| --- | --- |
| [prism-plugin-sdk](https://github.com/Rokid-Prism/prism-plugin-sdk) | 构建插件的 PluginBridge SDK，以三种语言发布：Go module（`github.com/Rokid-Prism/prism-plugin-sdk`）、npm 包（`@rokid-prism/pluginbridge-plugin-sdk`）、PyPI 包（`rokid-pluginbridge-plugin-sdk`）。同时定义插件 manifest 规范与一致性测试套件。 |
| [prism-plugin-claude-code](https://github.com/Rokid-Prism/prism-plugin-claude-code) | Claude Code 官方插件 — 协议原生，通过 ACP 对接本地 `claude` 运行时 |
| [prism-plugin-codex](https://github.com/Rokid-Prism/prism-plugin-codex) | Codex 官方插件 — 通过桌面自动化操作 Codex Desktop，浏览会话、读取历史、继续线程 |
| [prism-plugin-hermes](https://github.com/Rokid-Prism/prism-plugin-hermes) | Hermes 官方插件 — 通过 Hermes 网关实现远程会话 |
| [prism-plugin-openclaw](https://github.com/Rokid-Prism/prism-plugin-openclaw) | OpenClaw 官方插件 — 协议原生，对接 OpenClaw 网关 |

### 插件如何工作

每个插件是一个由 `pluginbridge-plugin.yaml` manifest 描述的小程序，以两种方式之一接入智能体：

- **协议原生** — 通过智能体自身的协议（API、RPC 或 CLI）通信，如 OpenClaw 网关、通过 ACP 对接的 Claude Code
- **桌面自动化** — 在没有开放协议时操作智能体的桌面应用，如 Codex

插件以 GitHub Releases 分发，Hub 会自动发现、安装并更新它们。详情见各仓库 README。

## 如何贡献

想让 Prism 支持更多、更好的智能体？有两种绝佳的参与方式：

### 1. 智能体更新时，为插件贡献适配

智能体迭代很快——一次版本更新就可能改变菜单、界面或行为。如果你在用的智能体更新了，而对应的 Prism 插件还没跟上，这就是一个完美的贡献机会：在插件仓库提一个 Issue 说明变化，或者直接提交 Pull Request 完成适配。

### 2. 为新智能体创建插件

希望 Prism 支持尚未覆盖的智能体？创建一个新仓库，用 [prism-plugin-sdk](https://github.com/Rokid-Prism/prism-plugin-sdk) 开发插件，发布 Release 并提交注册到 Hub 的插件目录。注册完成后，所有 Prism 用户都能发现并安装你的插件。

**Pull Request**：fork 仓库 → 新建分支 → 提交 PR。提交信息请遵循 [Conventional Commits](https://www.conventionalcommits.org)（`feat:`、`fix:`、`chore:`），与现有提交历史保持一致。本组织所有公开仓库均采用 MIT 协议，贡献同样按 MIT 授权。

## 协议

本组织所有公开仓库均基于 [MIT License](https://opensource.org/license/mit) 发布。
