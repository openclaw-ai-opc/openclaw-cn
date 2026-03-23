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



🦞 OpenClaw — 个人 AI 助手
智能赋能，随心所用！
OpenClaw 是一款可在自有设备上部署运行的个人 AI 助手，能在你日常使用的各类通讯渠道中为你答疑解惑（支持 WhatsApp、电报、Slack、Discord、谷歌聊天、Signal、iMessage、BlueBubbles、IRC、微软 Teams、Matrix、飞书、LINE、Mattermost、Nextcloud Talk、Nostr、群晖聊天、Tlon、Twitch、Zalo、Zalo 个人版、网页聊天）。它可在 macOS/iOS/Android 系统上实现语音交互，还能渲染由你操控的实时画布。网关仅作为控制面存在，核心产品体验聚焦于 AI 助手本身。
如果你需要一款本地化、响应快、全天候在线的个人单用户 AI 助手，OpenClaw 便是你的理想之选。
官网 · 文档 · 产品愿景 · 深度维基 · 快速上手 · 版本更新 · 功能展示 · 常见问题 · 新手指引 · Nix 部署 · Docker 部署 · Discord 社区
推荐部署方式：在终端中执行 openclaw onboard 命令。OpenClaw 新手指引工具会逐步引导你完成网关、工作区、通讯渠道和技能的配置，是官方推荐的命令行部署方式，支持macOS、Linux 和 Windows（强烈推荐通过 WSL2 运行） 系统，兼容 npm、pnpm 或 bun 包管理器。首次安装？从这里开始：快速上手
赞助方
表格
开放人工智能	维尔塞尔	铁匠科技	凸面科技
订阅服务（OAuth 授权）：
开放人工智能（ChatGPT/Codex 大模型）
模型使用说明：尽管本项目支持多款大模型及服务商，但为获得最佳使用体验、降低提示词注入风险，建议使用你可访问的最新一代高性能大模型。详见新手指引。
大模型配置（选型 + 授权）
模型配置及命令行操作：大模型相关文档
授权配置轮替（OAuth 授权 / API 密钥）及故障回退：模型故障回退方案
推荐安装方式
运行环境：Node 24（推荐版本） 或 Node 22.16 及以上版本
bash
运行
npm install -g openclaw@latest
# 或使用pnpm：pnpm add -g openclaw@latest

openclaw onboard --install-daemon
OpenClaw 新手指引工具会自动安装网关守护进程（launchd/systemd 用户服务），确保服务全天候运行。
快速开始（极简版）
运行环境：Node 24（推荐版本） 或 Node 22.16 及以上版本
完整新手教程（含授权、设备配对、渠道配置）：快速上手
bash
运行
# 初始化部署并安装守护进程
openclaw onboard --install-daemon

# 启动网关（指定端口18789，开启详细日志）
openclaw gateway --port 18789 --verbose

# 发送消息给AI助手
openclaw message send --to +1234567890 --message "来自OpenClaw的问候"
# 与AI助手对话（消息可同步至任意已连接的通讯渠道）
openclaw agent --message "生成一份发货核对清单" --thinking high
版本升级？参考更新指南（升级后建议执行 openclaw doctor 命令检查环境）。
开发版本渠道
稳定版：带版本标签的正式发布版（格式为v年.月.日或v年.月.日-补丁号），对应 npm 的latest标签。
测试版：预发布版本（格式为v年.月.日-beta.版本号），对应 npm 的beta标签（可能无 macOS 客户端安装包）。
开发版：主分支最新开发版本，对应 npm 的dev标签（仅发布时可用）。
切换版本渠道（支持 Git+npm）：执行 openclaw update --channel stable|beta|dev 命令。详细说明：开发版本渠道文档。
从源码构建（开发环境）
从源码构建时，推荐使用pnpm包管理器，也可选择 Bun 直接运行 TypeScript 代码。
bash
运行
# 克隆仓库
git clone https://github.com/openclaw/openclaw.git
cd openclaw

# 安装依赖
pnpm install
# 构建UI界面（首次运行会自动安装UI相关依赖）
pnpm ui:build
# 构建项目
pnpm build

# 初始化部署并安装守护进程
pnpm openclaw onboard --install-daemon

# 开发热更模式（源码/配置文件修改后自动重启）
pnpm gateway:watch
说明：pnpm openclaw ... 命令通过tsx直接运行 TypeScript 代码，pnpm build 命令会在dist/目录生成编译文件，可通过 Node 或打包后的openclaw可执行文件运行。
安全默认配置（私信访问权限）
OpenClaw 可连接各类真实的通讯平台，请将所有收到的私信视为不可信输入。
完整安全指南：安全配置文档
电报 / WhatsApp/Signal/iMessage/ 微软 Teams/Discord/ 谷歌聊天 / Slack 的默认安全策略：
私信配对验证（配置项dmPolicy="pairing" / channels.discord.dmPolicy="pairing" / channels.slack.dmPolicy="pairing"；旧版配置：channels.discord.dm.policy、channels.slack.dm.policy）：陌生发送者会收到一个简短的配对码，AI 助手不会处理其发送的消息。
通过验证：执行 openclaw pairing approve <渠道名> <配对码> 命令，验证通过后发送者会被加入本地白名单。
公开私信访问：需手动开启，设置dmPolicy="open"并在渠道白名单中添加"*"（配置项allowFrom / channels.discord.allowFrom / channels.slack.allowFrom；旧版配置：channels.discord.dm.allowFrom、channels.slack.dm.allowFrom）。
执行 openclaw doctor 命令，可检查出配置不当、存在安全风险的私信策略。
核心功能亮点
本地化优先的网关：为会话、通讯渠道、工具和事件提供统一的控制面。
多渠道收件箱：一站式整合 WhatsApp、电报、Slack、Discord、谷歌聊天、Signal、BlueBubbles（iMessage）、iMessage（旧版）、IRC、微软 Teams、Matrix、飞书、LINE、Mattermost、Nextcloud Talk、Nostr、群晖聊天、Tlon、Twitch、Zalo、Zalo 个人版、网页聊天、macOS、iOS/Android 等渠道。
多智能体路由：将不同渠道 / 账号 / 联系人的消息路由至相互隔离的智能体（独立工作区 + 单智能体专属会话）。
语音唤醒 + 语音对话模式：macOS/iOS 系统支持唤醒词唤醒，Android 系统支持连续语音交互（默认使用 ElevenLabs 语音引擎，系统 TTS 为备用方案）。
实时画布：由 AI 智能体驱动的可视化工作区，集成 A2UI 界面。
原生工具支持：内置浏览器、画布、节点管理、定时任务、会话管理，及 Discord/Slack 操作工具。
配套客户端：macOS 菜单栏客户端 + iOS/Android 节点端。
新手引导 + 技能体系：以引导式部署为基础，支持内置、托管、工作区专属等多种技能类型。
已实现的核心功能模块
核心平台
网关 WebSocket 控制面：支持会话管理、在线状态、配置管理、定时任务、WebHook，集成控制界面和画布宿主功能。
命令行界面：提供网关、智能体、消息发送、新手引导、环境检测等命令。
Pi 智能体运行时：采用 RPC 模式，支持工具流和块流传输。
会话模型：main主会话用于一对一聊天，支持群聊隔离、激活模式、队列模式、消息回执；群聊规则详见群聊配置。
媒体处理流水线：支持图片 / 音频 / 视频处理、转录钩子、文件大小限制、临时文件生命周期管理；音频处理详情：音频相关文档。
通讯渠道
全渠道支持：WhatsApp（基于 Baileys）、电报（基于 grammY）、Slack（基于 Bolt）、Discord（基于 discord.js）、谷歌聊天（基于 Chat API）、Signal（基于 signal-cli）、BlueBubbles（iMessage 推荐方案）、iMessage（旧版 imsg）、IRC、微软 Teams、Matrix、飞书、LINE、Mattermost、Nextcloud Talk、Nostr、群晖聊天、Tlon、Twitch、Zalo、Zalo 个人版、网页聊天。
群聊路由：支持 @唤醒、回复标签、按渠道分块和路由；渠道规则详见渠道配置。
客户端 + 节点端
macOS 客户端：菜单栏网关控制、语音唤醒 / 一键对讲、语音对话悬浮窗、网页聊天、调试工具、远程网关控制。
iOS 节点端：支持画布、语音唤醒、语音对话、相机、录屏、Bonjour 设备配对。
Android 节点端：包含连接页（配码 / 手动配置）、聊天会话、语音页、画布、相机 / 录屏，支持 Android 设备指令（通知 / 定位 / 短信 / 照片 / 联系人 / 日历 / 运动 / 应用更新）。
macOS 节点模式：支持系统命令执行 / 通知，及画布 / 相机曝光控制。
工具 + 自动化
浏览器控制：专属 OpenClaw Chrome/Chromium 浏览器，支持截图、操作、文件上传、配置文件管理。
画布：支持 A2UI 界面推送 / 重置、代码执行、截图。
节点工具：相机拍照 / 录屏、屏幕录制、定位获取、消息通知。
定时任务 + 唤醒、WebHook、Gmail 发布 / 订阅。
技能平台：支持内置、托管、工作区专属技能，集成安装权限控制 + 可视化界面。
运行时 + 安全
渠道路由、重试策略、流传输 / 分块传输。
在线状态、输入状态提示、使用量统计。
大模型管理、模型故障回退、会话清理。
安全配置、问题排查。
运维 + 打包
控制界面 + 网页聊天：由网关直接提供服务，无需额外部署。
远程访问：支持 Tailscale Serve/Funnel 或 SSH 隧道，集成令牌 / 密码认证。
声明式配置：支持 Nix 模式实现配置即代码；基于 Docker 的部署方案。
环境检测：支持迁移检测、日志管理。
工作原理（极简版）
plaintext
各类通讯渠道（WhatsApp/电报/Slack/飞书等）
 │
 ▼
┌───────────────────────────────┐
│ 网关 │
│ （控制面） │
│ 本地地址：ws://127.0.0.1:18789 │
└──────────────┬────────────────┘
 │
 ├─ Pi智能体（RPC模式）
 ├─ 命令行工具（openclaw 命令）
 ├─ 网页聊天界面
 ├─ macOS客户端
 └─ iOS / Android节点端
核心子系统
网关 WebSocket 网络：为所有客户端、工具、事件提供统一的 WebSocket 控制面（运维文档：网关运行手册）。
Tailscale 远程访问：通过 Serve/Funnel 实现网关面板和 WebSocket 的远程访问（远程配置：远程访问文档）。
浏览器控制：由 OpenClaw 托管的 Chrome/Chromium 浏览器，基于 CDP 协议实现控制。
画布 + A2UI：由 AI 智能体驱动的可视化工作区（A2UI 宿主：画布 / A2UI 文档）。
语音唤醒 + 语音对话模式：macOS/iOS 系统支持唤醒词唤醒，Android 系统支持连续语音交互。
节点工具：支持画布、相机拍照 / 录屏、屏幕录制、定位获取、消息通知，macOS 系统独享系统命令执行 / 系统通知功能。
Tailscale 网关面板访问
OpenClaw 可自动配置 Tailscale 的Serve（仅内网访问）或Funnel（公网访问）功能，网关仍绑定本地回环地址。配置项gateway.tailscale.mode可选值：
off：关闭 Tailscale 自动化（默认值）。
serve：通过tailscale serve实现内网 HTTPS 访问（默认使用 Tailscale 身份头认证）。
funnel：通过tailscale funnel实现公网 HTTPS 访问（强制要求开启密码认证）。
注意事项：
启用 Serve/Funnel 功能时，gateway.bind必须保持为回环地址（OpenClaw 会强制校验）。
可通过设置gateway.auth.mode: "password"或gateway.auth.allowTailscale: false，强制 Serve 模式要求密码认证。
Funnel 模式仅在设置gateway.auth.mode: "password"后才能启动。
可选配置：gateway.tailscale.resetOnExit，网关关闭时自动还原 Serve/Funnel 配置。
详细说明：Tailscale 配置指南 · 网页界面
远程网关部署（推荐 Linux）
你可以在轻量 Linux 实例上部署网关，客户端（macOS、命令行、网页聊天）可通过Tailscale Serve/Funnel或SSH 隧道连接，设备节点（macOS/iOS/Android）仍可正常配对，按需执行设备本地操作。
网关主机：默认运行执行工具和渠道连接服务。
设备节点：通过node.invoke执行设备本地操作（系统命令、相机、录屏、通知）。
简单来说：执行类操作在网关主机运行，设备专属操作在设备本地运行。
详细说明：远程访问文档 · 节点工具 · 安全配置
基于网关协议的 macOS 权限控制
macOS 客户端可运行在节点模式，并通过网关 WebSocket 向服务端上报自身能力和权限映射（node.list / node.describe接口），客户端可通过node.invoke执行本地操作：
system.run：执行本地命令，返回标准输出 / 标准错误 / 退出码；若操作需要录屏权限，需设置needsScreenRecording: true，否则会返回PERMISSION_MISSING权限缺失错误。
system.notify：发送系统通知，若通知权限被拒绝则执行失败。
canvas.*、camera.*、screen.record、location.get等操作同样通过node.invoke路由，且遵循 macOS TCC 权限管理规则。
高权限 bash 操作（主机权限）与 macOS TCC 权限相互独立：
启用并加入白名单后，可通过/elevated on|off命令按会话切换高权限模式。
网关会通过sessions.patch（WebSocket 方法）持久化会话的高权限状态，同时保存的还有思考等级、日志详细度、大模型选择、发送策略、群聊激活模式等配置。
详细说明：节点工具 · macOS 客户端 · 网关协议
智能体间协作（sessions_* 工具）
借助该工具，可在不同会话间协同工作，无需在多个聊天界面间切换。
sessions_list — 发现活跃会话（智能体）及其元数据。
sessions_history — 获取指定会话的聊天记录。
sessions_send — 向其他会话发送消息；支持可选的回执交互 + 执行步骤通知（REPLY_SKIP跳过回执、ANNOUNCE_SKIP跳过通知）。
详细说明：会话工具文档
技能仓库（ClawHub）
ClawHub 是一个轻量级的技能仓库，启用后，AI 智能体可自动搜索技能，并根据需要拉取新技能。
ClawHub 技能仓库
聊天指令
可在 WhatsApp / 电报 / Slack / 谷歌聊天 / 微软 Teams / 网页聊天中发送以下指令（群聊指令仅群主可执行）：
/status — 查看会话简要状态（使用的大模型 + 令牌消耗，支持显示费用）
/new 或 /reset — 重置当前会话
/compact — 压缩会话上下文（生成摘要）
/think <等级> — 设置思考等级：off|minimal|low|medium|high|xhigh（仅 GPT-5.2 + Codex 模型支持）
/verbose on|off — 开启 / 关闭详细日志
/usage off|tokens|full — 设置每响应底部的使用量统计展示模式
/restart — 重启网关（群聊中仅群主可执行）
/activation mention|always — 切换群聊激活模式（仅群聊可用，@唤醒 / 始终激活）
配套客户端（可选）
仅部署网关即可获得完整的 AI 助手体验，所有配套客户端均为可选，用于增强功能体验。
若你计划构建 / 运行配套客户端，请参考以下平台运行手册。
macOS 客户端（OpenClaw.app）（可选）
菜单栏网关控制和健康状态监控。
语音唤醒 + 一键对讲悬浮窗。
网页聊天 + 调试工具。
基于 SSH 的远程网关控制。
注意：为保证 macOS 权限在重新构建后仍有效，需要使用签名构建包（详见macOS 权限配置）。
iOS 节点端（可选）
通过网关 WebSocket 实现设备配对（节点模式）。
语音触发转发 + 画布界面。
通过openclaw nodes …命令进行控制。
运行手册：iOS 设备连接。
Android 节点端（可选）
通过设备配对（openclaw devices ...命令）以 WebSocket 节点模式连接。
提供连接 / 聊天 / 语音页面，集成画布、相机、录屏功能，支持 Android 设备专属指令集。
运行手册：Android 设备连接。
智能体工作区 + 技能
工作区根目录：~/.openclaw/workspace（可通过配置项agents.defaults.workspace修改）。
注入式提示词文件：AGENTS.md、SOUL.md、TOOLS.md。
技能目录：~/.openclaw/workspace/skills/<技能名>/SKILL.md。
配置示例
极简版~/.openclaw/openclaw.json配置文件（仅指定大模型 + 默认配置）：
json
{
  "agent": {
    "model": "anthropic/claude-opus-4-6"
  }
}
完整配置参考（所有配置项 + 示例）。
安全模型（重点）
默认策略：主会话的工具在网关主机上运行，因此仅你自己使用时，AI 智能体拥有主机的完整访问权限。
群聊 / 渠道安全：设置agents.defaults.sandbox.mode: "non-main"，可让非主会话（群聊 / 其他渠道）在按会话隔离的 Docker 沙箱中运行；此时 bash 命令会在 Docker 容器内执行。
沙箱默认配置：白名单包含bash、process、read、write、edit、sessions_list、sessions_history、sessions_send、sessions_spawn；黑名单包含browser、canvas、nodes、cron、discord、gateway。
详细说明：安全指南 · Docker + 沙箱 · 沙箱配置
WhatsApp 渠道配置
设备绑定：执行pnpm openclaw channels login命令（凭证保存在~/.openclaw/credentials目录）。
访问控制：通过配置项channels.whatsapp.allowFrom添加可访问 AI 助手的白名单。
群聊配置：若设置channels.whatsapp.groups，则该配置为群聊白名单；添加"*"表示允许所有群聊。
电报渠道配置
令牌配置：设置环境变量TELEGRAM_BOT_TOKEN或配置项channels.telegram.botToken（环境变量优先级更高）。
可选配置：设置channels.telegram.groups（可搭配channels.telegram.groups."*".requireMention开启 @唤醒）；设置后该配置为群聊白名单（添加"*"表示允许所有群聊）。也可根据需要设置channels.telegram.allowFrom、channels.telegram.webhookUrl和channels.telegram.webhookSecret。
json
{
  "channels": {
    "telegram": {
      "botToken": "123456:ABCDEF"
    }
  }
}
Slack 渠道配置
设置环境变量SLACK_BOT_TOKEN + SLACK_APP_TOKEN，或配置项channels.slack.botToken + channels.slack.appToken。
Discord 渠道配置
令牌配置：设置环境变量DISCORD_BOT_TOKEN或配置项channels.discord.token。
可选配置：设置commands.native、commands.text、commands.useAccessGroups，及channels.discord.allowFrom、channels.discord.guilds、channels.discord.mediaMaxMb等。
json
{
  "channels": {
    "discord": {
      "token": "1234abcd"
    }
  }
}
Signal 渠道配置
需提前安装signal-cli，并在配置文件中添加channels.signal配置段。
BlueBubbles（iMessage）渠道配置
推荐的 iMessage 集成方案。
配置项channels.bluebubbles.serverUrl + channels.bluebubbles.password，并设置 WebHook 地址channels.bluebubbles.webhookPath。
BlueBubbles 服务端需运行在 macOS 系统，网关可运行在 macOS 或其他系统。
iMessage（旧版）渠道配置
基于imsg的 macOS 专属旧版集成方案（需提前登录 Messages 应用）。
若设置channels.imessage.groups，则该配置为群聊白名单；添加"*"表示允许所有群聊。
微软 Teams 渠道配置
配置 Teams 应用 + 机器人框架，然后在配置文件中添加msteams配置段。
访问控制：通过msteams.allowFrom设置可访问的白名单；通过msteams.groupAllowFrom或msteams.groupPolicy: "open"配置群聊访问权限。
网页聊天配置
基于网关 WebSocket 实现，无需单独配置端口 / 地址。
** 浏览器控制（可选）** 配置示例：
json
{
  "browser": {
    "enabled": true,
    "color": "#FF4500"
  }
}
官方文档
完成新手引导后，可参考以下进阶文档深入学习：
文档索引：快速导航，了解各功能模块位置。
架构概述：学习网关 + 协议模型的核心设计。
完整配置参考：包含所有配置项及使用示例。
网关运行手册：标准化的网关运维指南。
网页界面：了解控制界面 / 网页聊天的工作原理及安全暴露方式。
远程访问：基于 SSH 隧道或内网的远程访问配置。
新手引导：跟随引导式部署完成快速配置。
WebHook：通过 WebHook 实现外部事件触发。
Gmail 发布 / 订阅：配置 Gmail 事件触发。
macOS 菜单栏客户端：macOS 客户端详细使用指南。
平台指南：Windows（WSL2）、Linux、macOS、iOS、Android
问题排查：常见故障的调试指南。
安全指南：暴露服务前的必看安全配置。
进阶文档（发现 + 控制）
服务发现 + 传输协议
Bonjour/mDNS 服务发现
网关配对
远程网关说明
控制界面
仪表盘
运维 & 问题排查
健康检查
网关锁
后台进程
浏览器问题排查（Linux）
日志管理
深度解析
智能体循环
在线状态
TypeBox 模式
RPC 适配器
消息队列
工作区 & 技能
技能配置
默认智能体配置
模板：智能体
模板：引导部署
模板：身份配置
模板：灵魂配置
模板：工具配置
模板：用户配置
平台内部实现
macOS 开发环境配置
macOS 菜单栏
macOS 语音唤醒
iOS 节点端
Android 节点端
Windows（WSL2）
Linux 客户端
邮件钩子（Gmail）
Gmail 发布 / 订阅文档
关于 Molty
OpenClaw 是为Molty打造的 AI 助手，Molty 是一只太空龙虾 AI 助手。🦞 由 Peter Steinberger 和社区开发者共同开发。
OpenClaw 官网
灵魂配置文档
作者主页
官方 X 账号
社区贡献
贡献指南、维护者信息及 PR 提交方式，请参考CONTRIBUTING.md。欢迎提交基于 AI / 氛围编码的 PR！🤖
特别感谢Mario Zechner的支持，以及其开发的pi-mono项目。同时感谢 Adam Doppelt 开发的 lobster.bot 项目。
感谢所有社区贡献者！
关于本项目
一款可部署在自有设备的个人 AI 助手，跨系统、跨平台，龙虾式智能体验。🦞
版本发布
暂无已发布版本
软件包
暂无已发布软件包
贡献者
暂无贡献者
开发语言占比
TypeScript 88.7%
Swift 7.0%
Kotlin 1.6%
Shell 1.0%
JavaScript 0.9%
CSS 0.5%
其他 0.3%
我可以帮你把这份中文 README 整理成Markdown 纯净版，移除所有外链和冗余格式，方便你直接替换仓库原文件，需要吗？
把这份中文 README 整理成Markdown 纯净版
🦞 OpenClaw — 个人 AI 助手
智能赋能，随心所用！
OpenClaw 是一款可在自有设备上部署运行的个人 AI 助手，能在你日常使用的各类通讯渠道中为你答疑解惑（支持 WhatsApp、电报、Slack、Discord、谷歌聊天、Signal、iMessage、BlueBubbles、IRC、微软 Teams、Matrix、飞书、LINE、Mattermost、Nextcloud Talk、Nostr、群晖聊天、Tlon、Twitch、Zalo、Zalo 个人版、网页聊天）。它可在 macOS/iOS/Android 系统上实现语音交互，还能渲染由你操控的实时画布。网关仅作为控制面存在，核心产品体验聚焦于 AI 助手本身。
如果你需要一款本地化、响应快、全天候在线的个人单用户 AI 助手，OpenClaw 便是你的理想之选。
推荐部署方式：在终端中执行 openclaw onboard 命令。OpenClaw 新手指引工具会逐步引导你完成网关、工作区、通讯渠道和技能的配置，是官方推荐的命令行部署方式，支持 macOS、Linux 和 Windows（强烈推荐通过 WSL2 运行） 系统，兼容 npm、pnpm 或 bun 包管理器。
大模型配置
支持多款大模型及服务商
为获得最佳使用体验、降低提示词注入风险，建议使用可访问的最新一代高性能大模型
支持授权配置轮替与故障回退
推荐安装方式
运行环境：Node 24（推荐） 或 Node 22.16 及以上
bash
运行
npm install -g openclaw@latest
# 或 pnpm：pnpm add -g openclaw@latest

openclaw onboard --install-daemon
OpenClaw 新手指引工具会自动安装网关守护进程，确保服务全天候运行。
快速开始（极简版）
bash
运行
# 初始化部署并安装守护进程
openclaw onboard --install-daemon

# 启动网关（指定端口 18789，开启详细日志）
openclaw gateway --port 18789 --verbose

# 发送消息给 AI 助手
openclaw message send --to +1234567890 --message "来自 OpenClaw 的问候"

# 与 AI 助手对话
openclaw agent --message "生成一份发货核对清单" --thinking high
升级后建议执行 openclaw doctor 检查环境。
开发版本渠道
稳定版：正式发布版，对应 npm latest
测试版：预发布版，对应 npm beta
开发版：主分支最新版，对应 npm dev
切换版本：
bash
运行
openclaw update --channel stable|beta|dev
从源码构建
bash
运行
git clone https://github.com/openclaw-ai-opc/openclaw-cn.git
cd openclaw-cn

pnpm install
pnpm ui:build
pnpm build

pnpm openclaw onboard --install-daemon
pnpm gateway:watch
安全默认配置（私信访问权限）
所有收到的私信均视为不可信输入。
默认安全策略：
私信配对验证：陌生用户需输入配对码，未验证不处理消息
通过验证：openclaw pairing approve <渠道名> <配对码>
公开私信访问：需手动开启 dmPolicy="open" 并配置白名单
可使用 openclaw doctor 检查安全风险。
核心功能亮点
本地化优先网关：统一管理会话、渠道、工具和事件
多渠道收件箱：支持国内外主流 IM 平台
多智能体路由：不同账号 / 联系人消息路由到独立智能体
语音唤醒 + 语音对话：支持 macOS/iOS/Android
实时画布：AI 驱动可视化工作区
原生工具支持：浏览器、画布、定时任务、会话管理
配套客户端：macOS 菜单栏客户端 + iOS/Android 节点端
新手引导 + 技能体系：支持多种技能类型
核心功能模块
核心平台
网关 WebSocket 控制面
完整命令行界面
Pi 智能体运行时
会话模型与群聊隔离
媒体处理流水线
通讯渠道
WhatsApp、电报、Slack、Discord、谷歌聊天、Signal、BlueBubbles、iMessage、IRC、微软 Teams、Matrix、飞书、LINE、Mattermost、Nextcloud Talk、Nostr、群晖聊天、Tlon、Twitch、Zalo、网页聊天等。
客户端与节点端
macOS 客户端：菜单栏控制、语音唤醒、悬浮窗
iOS 节点端：画布、语音、相机、录屏
Android 节点端：全功能移动端控制
工具与自动化
浏览器控制
画布与 A2UI
相机、录屏、定位、通知
定时任务、WebHook、Gmail 订阅
技能平台与权限管理
工作原理
plaintext
各类通讯渠道
    ↓
┌───────────────────────┐
│         网关          │
│  本地 ws://127.0.0.1:18789  │
└───────────┬───────────┘
            ├─ Pi 智能体
            ├─ 命令行工具
            ├─ 网页聊天
            └─ 各平台客户端
Tailscale 网关面板访问
支持通过 Tailscale Serve / Funnel 实现内网 / 公网访问网关面板：
off：关闭
serve：内网 HTTPS
funnel：公网 HTTPS（需密码）
远程网关部署
可在 Linux 服务器部署网关，客户端通过 Tailscale 或 SSH 隧道连接。
网关主机：运行工具与渠道连接
设备节点：执行本地操作（相机、录屏、系统命令等）
智能体间协作
sessions_list：列出活跃会话
sessions_history：查看聊天记录
sessions_send：向其他会话发消息
技能仓库（ClawHub）
轻量级技能仓库，AI 可自动搜索并拉取新技能。
聊天指令
/status：查看会话状态与用量
/new / /reset：重置会话
/compact：压缩上下文
/think <等级>：设置思考强度
/verbose on|off：详细日志开关
/usage：用量统计显示
/restart：重启网关
/activation：群聊唤醒模式
智能体工作区 + 技能
工作区目录：~/.openclaw/workspace
提示词文件：AGENTS.md、SOUL.md、TOOLS.md
技能目录：~/.openclaw/workspace/skills/
配置示例
json
{
  "agent": {
    "model": "anthropic/claude-opus-4-6"
  }
}
安全模型
默认：主会话工具在网关主机运行，拥有完整权限
群聊 / 沙箱：可配置 Docker 沙箱隔离非主会话
支持工具白名单 / 黑名单
渠道配置简要说明
WhatsApp
登录：openclaw channels login
白名单：channels.whatsapp.allowFrom
电报
设置 TELEGRAM_BOT_TOKEN 或配置文件写入 token
Slack / Discord
配置对应 Bot Token 即可
Signal
需提前安装 signal-cli
BlueBubbles / iMessage
支持 macOS 集成与远程服务端
网页聊天
基于网关 WebSocket，无需额外端口
关于项目
OpenClaw 是一款可部署在自有设备的个人 AI 助手，跨系统、跨平台，提供本地化智能体验。
由 Peter Steinberger 与社区开发者共同开发。
社区贡献
欢迎提交 PR 与参与共建，详见贡献指南。
开发语言占比
TypeScript 88.7%
Swift 7.0%
Kotlin 1.6%
Shell 1.0%
JavaScript 0.9%
CSS 0.5%
其他 0.3%
