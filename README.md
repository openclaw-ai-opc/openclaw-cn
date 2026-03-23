# 🦞 OpenClaw — Personal AI Assistant

<p align="center">
    <picture>
        <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/openclaw-logo-text-dark.svg">
        <img src="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/openclaw-logo-text.svg" alt="OpenClaw" width="500">
    </picture>
</p>

<p align="center">
  <strong>EXFOLIATE! EXFOLIATE!</strong>
</p>

<p align="center">
  <a href="https://github.com/openclaw/openclaw/actions/workflows/ci.yml?branch=main"><img src="https://img.shields.io/github/actions/workflow/status/openclaw/openclaw/ci.yml?branch=main&style=for-the-badge" alt="CI status"></a>
  <a href="https://github.com/openclaw/openclaw/releases"><img src="https://img.shields.io/github/v/release/openclaw/openclaw?include_prereleases&style=for-the-badge" alt="GitHub release"></a>
  <a href="https://discord.gg/clawd"><img src="https://img.shields.io/discord/1456350064065904867?label=Discord&logo=discord&logoColor=white&color=5865F2&style=for-the-badge" alt="Discord"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge" alt="MIT License"></a>
</p>



# OpenClaw（中文说明）

## 📌 项目简介
OpenClaw 是一个开源的 AI Agent（智能代理）框架，用于构建可以自动执行任务的 AI 助手。它可以调用大语言模型（如 OpenAI、Claude 等），并通过各种工具完成自动化工作。

该项目完全开源，支持本地运行，强调隐私和可扩展性。

---

## 🚀 功能特点

- 🤖 自动化 AI Agent（可执行任务）
- 💬 支持多平台聊天（Telegram / Discord / Slack 等）
- 🧠 持久记忆（记住用户偏好）
- 🌐 浏览网页、操作系统
- 🔧 插件/工具扩展能力
- 🔐 本地运行，数据可控

---

## 📁 项目结构

- `/cmd`：CLI 入口
- `/gateway`：网关服务
- `/agents`：Agent 实现
- `/providers`：模型接入
- `/channels`：聊天渠道集成
- `/tools`：工具系统

---

## ⚙️ 安装方法

### 前置要求
- Go 1.22+
- Node.js 22+
- Git

### 安装步骤

```bash
# 克隆仓库
git clone https://github.com/openclaw/openclaw.git
cd openclaw

# 安装依赖
go mod download

# 构建
cd gateway && go build -o openclaw-gateway .
cd ..
```

或者使用脚本安装：

```bash
curl -fsSL https://openclaw.ai/install.sh | bash
```

---

## ⚠️ 常见问题

- gateway 无法启动 → 检查配置
- gateway.connect 失败 → 检查网络或模式
- 安装失败 → 检查依赖版本

---

## 🤝 贡献指南

- Fork 仓库
- 创建新分支
- 遵循代码规范（make lint）
- 编写测试
- 提交 PR

---

## 📚 扩展资源

- 官方文档
- Skills 插件系统
- 社区仓库（ClawHub）

---

## 🧠 总结

OpenClaw 是一个高度灵活的 AI 自动化框架，适合开发：

- AI 助手
- 自动化工作流
- 聊天机器人
- 私人 AI 系统

