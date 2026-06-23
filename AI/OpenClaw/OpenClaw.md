# 定义与简介
OpenClaw是一个开源的自主人工智能（AI）虚拟助理软件项目，因其图标是一只红色龙虾又被称作“龙虾”。OpenClaw由奥地利软件工程师彼得·斯坦伯格开发，最初于2025年末以Clawdbot的名字在GitHub上发布，后更名为Moltbot，最终定为现名。

2026年初，该AI项目因能够根据用户指令，在应用程序和在线服务中自主处理复杂任务而受到广泛关注。
## 功能
OpenClaw被设计为可代替用户执行任务的自主人工智能虚拟助理软件，而非只是对话式聊天机器人。其可部署在MacOS、Windows等本地设备上，并能够调用其他AI大模型与应用程序接口（API），通过WhatsApp、Telegram、Signal、Discord等即时通讯平台接收用户发送的文本指令，实现安排日程、发送消息、整理文件、编写代码等工作。OpenClaw在本地存储配置数据和交互历史，从而拥有较持久的记忆能力。

OpenClaw 拥有对本地系统的操作权限，因此它能做的事情远超普通聊天机器人：

* 文件与系统操作
	* 读写文件：自动整理文件夹、批量重命名文件、备份重要数据。
	* 执行命令：在终端中运行脚本、安装软件、管理系统进程。

* 浏览器自动化
	* 网页操作：自动登录网站、填写表单、抓取数据、监控价格变化。
	* 信息检索：根据指令搜索特定信息，并整理成报告。

* 办公与开发
	- 代码编写：根据需求生成代码片段，甚至修复 Bug。
	- 邮件处理：自动发送邮件、整理收件箱、过滤垃圾邮件。
	- 文档处理：自动生成日报、整理会议纪要。

* 远程控制与定时任务
	- 远程指令：即使你不在电脑前，也可以通过手机发消息让它执行任务。
	- 定时任务：设置定时任务，让它每天自动为你生成天气简报或新闻摘要。

## 风险
OpenClaw在运行时通常需要获取本地设备较高的权限和自主权，因此小的配置错误也可能引发数据泄露，此外还面临提示词攻击、特权提升等风险，并存在多个安全漏洞。

2026年1月29日，Axios的一篇报道指出数百个OpenClaw控制面板因配置错误已暴露在开放互联网上，使得入侵者可以访问对话记录、API密钥和凭证，甚至以用户身份运行命令。

2026年2月23日，Meta一名AI安全研究员通过手机会话指示OpenClaw协助自己整理电子邮箱，并规定“在我指示之前不要执行任何操作”。但由于邮箱内容太大，OpenClaw触发了“上下文压缩”机制并忽视了其指令，导致电子邮箱差点被清空。

2026年2月5日，中华人民共和国工业和信息化部指出OpenClaw在默认或不当配置情况下存在较高安全风险，并建议相关单位和用户使用时充分核查公网暴露、权限配置及凭证管理情况；随后，工业和信息化部下属中国信息通信研究院副院长魏亮在采访中表示应审慎使用OpenClaw；国家互联网应急中心也表示OpenClaw存在四大风险。另据彭博社报道，中国官方已限制国有企业和政府机构在办公电脑上运行OpenClaw。大陆部分高校亦禁止在校内使用OpenClaw。香港网络安全事故协调中心表示应警惕OpenClaw引发的安全风险；香港数字政策办公室也建议使用OpenClaw应采取充足的安全措施。中国国家互联网应急中心随后发布提示，建议普通用户使用专用设备、虚拟机或容器安装OpenClaw，不应在日常办公电脑上安装。

# 资料链接
- 官网：https://openclaw.ai/
- Github：https://github.com/openclaw
- 文档中心：https://docs.openclaw.ai/start/getting-started
- 技能中心：https://clawhub.ai/
- 社区中心：https://discord.com/invite/clawd

# 快速开始
## 概况
OpenClaw 是一个**自托管 Gateway 网关**，可将你喜爱的聊天应用和渠道表面——包括内置渠道，以及内置或外部渠道插件（如 Discord、Google Chat、iMessage、Matrix、Microsoft Teams、Signal、Slack、Telegram、WhatsApp、Zalo 等）——连接到像 Pi 这样的 AI 编码智能体。你只需在自己的机器（或服务器）上运行一个 Gateway 网关进程，它就会成为你的消息应用与始终可用的 AI 助手之间的桥梁。

### 使用
适合开发者和高级用户，他们希望拥有一个可以随时随地发消息的个人 AI 助手——同时又不放弃对自己数据的控制，也不依赖托管服务。

### 特性
- **自托管**：运行在你的硬件上，遵循你的规则。
- **多渠道**：一个 Gateway 网关可同时服务内置渠道以及内置或外部渠道插件。
- **智能体原生**：专为支持工具使用、会话、记忆和多智能体路由的编码智能体打造。
- **开源**：采用 MIT 许可证，由社区驱动。

### 要求
Node 24（推荐），或为了兼容性使用 Node 22 LTS（`22.14+`），你所选提供商的一个 API key，以及 5 分钟时间。为了获得最佳质量与安全性，请使用最新一代中能力最强的模型。

## 工作原理
![工作原理图](图片/工作原理图.png)
Gateway 网关是会话、路由和渠道连接的唯一事实来源。
### 系统架构
OpenClaw 采用五大功能模块的微服务架构：

```text
┌─────────────────────────────────────────────────────────┐
│                    消息渠道层                              │
│  WhatsApp │ Telegram │ Slack │ Discord │ 飞书 │ 钉钉      │
└────────────────────────┬────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────┐
│              Gateway（核心控制平面）                       │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌───────────┐  │
│  │ Sessions │ │ Channels │ │  Tools   │ │  Events   │  │
│  └──────────┘ └──────────┘ └──────────┘ └───────────┘  │
│                    localhost:18789                       │
└────────────┬───────────────────┬────────────────────────┘
             │                   │
     ┌───────▼───────┐   ┌──────▼──────┐
     │   Agent 层     │   │  Nodes 层   │
     │ (LLM 决策引擎) │   │ (设备端点)   │
     │ Claude/GPT/    │   │ iOS/Android │
     │ Ollama/Qwen    │   │ Camera/GPS  │
     └───────┬───────┘   └─────────────┘
             │
     ┌───────▼───────┐
     │   Skills 层    │
     │  (插件工具包)   │
     │ Shell/Browser/ │
     │ File/Web/API   │
     └───────────────┘
```

**关键组件说明**：

- **Gateway**: 单一控制平面，所有消息经由此路由，管理认证和会话
- **Agent**: 连接 LLM（Claude、GPT、Ollama 等），理解上下文并制定执行计划
- **Skills**: JS/TS 可扩展工具包，支持 Shell 命令、文件操作、浏览器控制等
- **Channels**: 连接各消息平台，提供统一消息接口
- **Nodes**: 在用户设备上运行的传感器/端点，暴露设备能力

### 架构术语说明

```text
用户/聊天软件/控制台/移动节点
        ↓
Channels
        ↓
Gateway：长驻进程、路由、认证、会话、WS/HTTP API
        ↓
Agent runtime：工作区、上下文、记忆、session、agent loop
        ↓
Model：LLM 推理
        ↕
Tools：执行动作
        ↑
Skills：给 agent 的工作说明
Plugins：扩展 channels / tools / model providers / hooks / skills
```

* Channels: 聊天/通信入口
  - 例如 Telegram、WhatsApp、Slack、Discord、Signal、iMessage、WebChat 等。每个 channel 通过 Gateway 接入，文本普遍支持，媒体和反应能力按平台不同。多个 channel 可以同时运行。
* Gateway: OpenClaw 的长驻守护进程和控制平面
  - 负责 channel/provider 连接、WebSocket/HTTP API、路由、认证、session、健康事件、插件路由、Control UI。默认本地端口是 127.0.0.1:18789。文档说它是 sessions、routing、channel connections 的 single source of truth。
* Agent: 被 Gateway 调度的 AI 助手实例/“脑”
  - 一个 agent 包含工作区、人格/说明文件、模型配置、认证资料、session 历史。默认是单 agent，也可以在一个 Gateway 中跑多个隔离 agent，并用 bindings 把不同 channel/account/peer 路由过去。
* Tools: 模型可调用的结构化动作函数
  - 如 exec、browser、web_search、message、image_generate、read/write/edit/apply_patch 等。工具让 agent 能读数据、改文件、发消息、操作浏览器或调用外部系统；只有通过策略过滤后的工具 schema 才会给模型看到。
* Skills: 给 agent 的 Markdown 工作说明包
  - 每个 skill 通常是一个目录里的 SKILL.md，包含 frontmatter 和正文，告诉 agent 何时、如何使用已有工具。它本身通常不新增能力，而是把流程、规范、检查清单注入 prompt。
* Plugins: 可安装的运行时扩展代码包
  - 插件可以新增 channels、model providers、tools、skills、hooks、语音、媒体生成、web search/fetch 等。来源可以是 ClawHub、npm、git、本地目录等。
* Model: agent 使用的大语言模型/推理后端
  - OpenClaw 用 provider/model 形式配置模型，例如 openai/gpt-5.5、anthropic/claude-opus-4-6。模型 provider 负责认证、模型目录和调用方式；OpenClaw 负责把上下文、技能、工具定义送入模型并执行工具循环。

总结: Tool 是“能做什么动作”，Skill 是“怎么做这类工作”，Plugin 是“给系统装上新能力”，Model 是“负责推理和决策的大脑”，Gateway 是“把所有这些接起来的中枢”。

### 与 codex 对比
OpenClaw 更像“自托管 AI agent 网关/路由器”：把 WhatsApp、Telegram、Slack、Discord、WebChat 等入口统一接到 agent。Codex 更像“OpenAI 官方 coding agent 产品/运行时”：重点在读代码、改代码、跑测试、代码审查、并行开发任务。两者不是完全同类，OpenClaw 甚至可以把 Codex 当作底层 agent runtime 来用。

```text
OpenClaw:
聊天软件/节点/网页 → Gateway → agent runtime → model + tools + skills/plugins → 回到各聊天 channel

Codex:
Codex app/CLI/IDE/web → 本地或云端工作区 → Codex agent/runtime → coding model + tools → diff/PR/测试结果
```

#### 核心定位对比
| 维度 | OpenClaw | Codex |
| --- | --- | --- |
| 产品定位 | 自托管、多渠道 AI agent Gateway | OpenAI 官方软件开发 agent |
| 第一入口 | 聊天软件、WebChat、移动/桌面节点、CLI、Control UI | Codex app、CLI、IDE extension、Codex web |
| 核心价值 | “随时从任意聊天入口唤起自己的 agent” | “在代码库里高质量完成开发、审查、调试、重构” |
| 部署方式 | 自己运行 Gateway，默认本地 127.0.0.1:18789 | 本地 app/CLI/IDE，也有 Codex Cloud |
| 扩展重点 | channel、provider、tool、skill、hook、agent harness | skills、plugins、MCP、shell/browser/computer-use、cloud tasks |
| 模型选择 | 多 provider，常用 provider/model，如 openai/gpt-5.5、anthropic/... | 官方推荐 Codex 模型，如 gpt-5.5，本地可配置模型；云端任务默认模型当前不可改 |
| 是否开源 | OpenClaw 是开源自托管项目 | Codex CLI/app-server 等组件开源，但 Codex 产品和模型是 OpenAI 托管体系的一部分 |
| 最适合   | 个人/团队想把 AI 助手接入各种聊天渠道 | 开发者想在 repo 内完成真实工程任务 |

#### 概念逐项映射
| OpenClaw 概念 | 在 OpenClaw 中 | Codex 中的近似物 | 关键差异 |
| --- | --- | --- | --- |
| Channels | Telegram、WhatsApp、Slack、Discord、Signal、iMessage、WebChat 等聊天入口，每个 channel 经 Gateway 接入 | Codex 没有同等“多聊天 channel”核心概念；它有 app/CLI/IDE/web，以及 GitHub/Slack/Linear 等集成 | OpenClaw 的 channel 是主战场；Codex 的入口主要围绕代码工作流 |
| Gateway | 长驻守护进程，负责 channel 连接、WebSocket API、路由、认证、session、节点、Control UI | Codex 有 app-server，为 rich clients 提供认证、历史、审批、流式事件 | OpenClaw Gateway 是多渠道中枢；Codex app-server 是 Codex 客户端集成协议，不负责 WhatsApp/Telegram 这类消息路由 |
| Agent | 	OpenClaw agent runtime 管理 workspace、session、bootstrap files、tools、skills、model routing | Codex 本身就是 coding agent，可读写代码、运行命令、审查、调试、自动化开发任务 | OpenClaw 的 agent 更“通用消息助手”；Codex agent 更“工程开发专家” |
| Tools | typed function，如 exec、browser、web_search、message、image_generate、apply_patch 等 | shell、apply patch、web search、MCP、computer use、browser、code tools 等 | shell、apply patch、web search、MCP、computer use、browser、code tools 等 |
| Skills | SKILL.md 指令包，教 agent 何时和如何使用工具 | Codex skills 也是 instructions/resources/scripts 的可复用工作流格式 | Codex skills 也是 instructions/resources/scripts 的可复用工作流格式 |
| Plugins | 可新增 channels、model providers、agent harnesses、tools、skills、hooks、语音、媒体、搜索等 | Codex plugins 打包 skills、app integrations、MCP servers | OpenClaw plugin 更底层、更运行时；Codex plugin 更像可安装的工作流/应用连接包 |
| Model | 多 provider 模型引用，provider/model | Codex 推荐 OpenAI coding models，本地可指定模型，Cloud 当前默认不可改 | OpenClaw 更 provider-agnostic；Codex 更深度绑定 OpenAI coding model 体验 |

#### 最重要的架构差别
OpenClaw 的中心是 Gateway。官方文档说它是 sessions、routing、channel connections 的 single source of truth，并且一个 Gateway 管理 WhatsApp、Telegram、Slack、Discord、Signal、iMessage、WebChat 等消息面。也就是说，它解决的是“我从哪里和 agent 对话、怎么路由到正确 agent、怎么回到原聊天平台”。

Codex 的中心是 coding agent runtime/client surface。官方定义 Codex 是 OpenAI 的软件开发 coding agent，可写代码、理解代码库、审查、调试、自动化开发任务；CLI 可在本机目录读写和运行代码，Codex web 可在云端后台并行执行任务。

#### 二者可以组合
OpenClaw 文档明确有 bundled codex plugin，可以让 OpenClaw 通过 Codex app-server 运行 OpenAI agent turns。此时边界大致是：

```text
Telegram/WhatsApp/Slack
        ↓
OpenClaw Gateway：channel、路由、会话镜像、媒体投递、OpenClaw 工具/审批
        ↓
Codex app-server：Codex thread、native tool continuation、native compaction、底层 agent execution
        ↓
OpenAI model，如 gpt-5.5
```

openai/gpt-5.5 是 model ref，codex 是 runtime，Telegram/Discord/Slack 等仍然是 communication surface。

## 功能
### 亮点
![关键能力](图片/关键能力.png)

### 完整列表

**渠道：**

- 内置渠道包括 Discord、Google Chat、iMessage（旧版）、IRC、Signal、Slack、Telegram、WebChat 和 WhatsApp
- 内置插件渠道包括适用于 iMessage 的 BlueBubbles、Feishu、LINE、Matrix、Mattermost、Microsoft Teams、Nextcloud Talk、Nostr、QQ Bot、Synology Chat、Tlon、Twitch、Zalo 和 Zalo Personal
- 可选的单独安装渠道插件包括 Voice Call 和 WeChat 等第三方软件包
- 第三方渠道插件可进一步扩展 Gateway 网关，例如 WeChat
- 支持基于提及激活的群聊
- 通过允许列表和配对机制保障私信安全

**智能体：**

- 具有工具流式传输的内置智能体运行时
- 按工作区或发送方隔离会话的多智能体路由
- 会话：私聊会合并到共享的 `main`；群组彼此隔离
- 针对长回复的流式传输与分块

**认证和提供商：**

- 35+ 模型提供商（Anthropic、OpenAI、Google 等）
- 通过 OAuth 的订阅认证（例如 OpenAI Codex）
- 自定义和自托管提供商支持（vLLM、SGLang、Ollama，以及任何兼容 OpenAI 或兼容 Anthropic 的端点）

**多媒体：**

- 图片、音频、视频和文档的输入与输出
- 共享的图片生成和视频生成能力表面
- 语音消息转录
- 支持多个提供商的文本转语音

**应用和界面：**

- WebChat 和浏览器 Control UI
- macOS 菜单栏配套应用
- iOS 节点，支持配对、Canvas、相机、屏幕录制、定位和语音
- Android 节点，支持配对、聊天、语音、Canvas、相机和设备命令

**工具和自动化：**

- 浏览器自动化、exec、沙箱隔离
- Web 搜索（Brave、DuckDuckGo、Exa、Firecrawl、Gemini、Grok、Kimi、MiniMax Search、Ollama Web 搜索、Perplexity、SearXNG、Tavily）
- Cron 作业和心跳调度
- Skills、插件和工作流管线（Lobster）
## 安装
### 要求
* Node.js — 推荐使用 Node 24（亦支持 Node 22.14 及更高版本）
* 来自模型提供商（如 Anthropic、OpenAI、Google 等）的 API 密钥 — 入门设置流程中将提示您提供

运行 `node --version` 命令以检查您的 Node 版本。Windows 用户请注意：原生 Windows 环境和 WSL2 均受支持。其中，WSL2 更加稳定，建议使用以获得完整的体验。

### 快速设置
1. 安装 OpenClaw

		curl -fsSL https://openclaw.ai/install.sh | bash

2. 运行引导

		openclaw onboard --install-daemon

	该向导将引导完成选择模型提供商、设置 API 密钥和配置网关的过程。

3. 验证网关运行

		openclaw gateway status

	应该能看到网关正在监听端口 18789。

4. 打开仪表板

		openclaw dashboard

	这会在浏览器中打开控制界面。如果界面能够加载，说明一切运行正常。

5. 发送消息

	在控制界面的聊天窗口中输入消息，即可收到 AI 的回复。如果想改用手机进行聊天，最快捷的设置渠道是 Telegram（仅需一个 Bot Token）。

## 引导说明
OpenClaw 提供了两条引导路径。这两条路径均涵盖了身份验证、网关以及可选的聊天频道配置——二者的区别仅在于您与设置流程的交互方式不同。
### 方式
![引导方式](图片/引导方式.png)
大多数用户应从 CLI 入门开始——它适用于所有环境，并能为您提供最大的控制权。

### 引导配置的内容
无论选择哪种路径，引导配置流程都会完成以下设置：
* 模型提供商与认证 — 为选定的提供商配置 API 密钥、OAuth 或设置令牌
* 工作区 — 用于存放代理文件、引导模板及记忆数据的目录
* 网关 — 端口、绑定地址及认证模式
* 通道（可选）— 内置及捆绑的聊天通道，例如 BlueBubbles、Discord、飞书（Feishu）、Google Chat、Mattermost、Microsoft Teams、Telegram、WhatsApp 等
* 守护进程（可选）— 后台服务，确保网关能够自动启动

### 引导CLI
在任意终端中运行：

	openclaw onboard

添加 `--install-daemon` 参数，即可一步到位同时安装后台服务。

### 使用自定义或未列出的模型
如果要使用的服务提供商未列入入驻向导中，请选择“自定义提供商”，并填写以下信息：

* API 兼容模式（兼容 OpenAI、兼容 Anthropic 或自动检测）
* 基础 URL 和 API 密钥
* 模型 ID（以及可选的别名）

多个自定义端点可以共存——每个端点均拥有独立的端点 ID。

## 引导CLI
通过 CLI 进行引导式设置，是配置 macOS、Linux 或 Windows（强烈推荐通过 WSL2）上 OpenClaw 的首选方式。它通过一套引导流程，即可一站式完成本地或远程网关连接、频道、技能以及工作区默认设置的配置。

	openclaw onboard

若需稍后重新配置：

	openclaw configure 
	openclaw agents add <name>

CLI 入门设置包含一个网页搜索配置步骤，您可以在此选择 Brave、DuckDuckGo、Exa、Firecrawl、Gemini、Grok、Kimi、MiniMax Search、Ollama Web Search、Perplexity、SearXNG 或 Tavily 等服务提供商。部分提供商需要 API 密钥，而另一些则无需密钥。也可以稍后通过运行 `openclaw configure --section web` 命令来进行配置。

### 快速入门 vs 高级模式
引导始于“快速入门”（默认设置）与“高级模式”（完全控制）的选择。

#### 快速入门
* 本地网关（回环模式）
* 工作区默认设置（或现有工作区）
* 网关端口：18789
* 网关认证令牌（自动生成，即使在回环模式下也是如此）
* 新本地部署的工具策略默认设置：`tools.profile: "coding"`（若已显式指定现有配置文件，则予以保留）
* DM 隔离默认设置：本地初始化时，若未显式设置 `session.dmScope`，则默认写入 `"per-channel-peer"`。
* Tailscale 暴露功能：关闭
* Telegram 与 WhatsApp 的 DM 默认启用白名单模式（系统将提示您输入手机号码）

#### 高级模式
公开每一个步骤（模式、工作区、网关、通道、守护进程、技能）。

### 引导配置的内容
本地模式（默认）将引导完成以下步骤：
1. 模型/认证 —— 选择任何受支持的提供商/认证流程（API 密钥、OAuth 或特定于提供商的手动认证），包括自定义提供商（兼容 OpenAI、兼容 Anthropic 或自动检测未知类型）。请选择一个默认模型。安全提示：如果该代理（Agent）需要运行工具或处理 Webhook/钩子内容，建议优先选用当前可用的最强大、最新一代的模型，并保持严格的工具策略。性能较弱或较旧的模型层级更容易受到“提示注入”（Prompt Injection）攻击。对于非交互式运行，使用 `--secret-input-mode ref` 参数可以将基于环境变量的引用存储在认证配置文件中，而非直接存储明文的 API 密钥值。在非交互式的引用模式下，必须设置相应的提供商环境变量；若未设置该环境变量却试图通过命令行参数直接传入密钥，程序将立即报错并终止运行。对于交互式运行，选择“密钥引用模式”允许您指定一个环境变量，或指定一个已配置的提供商引用（可以是文件路径或可执行命令），并在保存前执行快速的预检验证。针对 Anthropic 服务，交互式的配置向导会将“Anthropic Claude CLI”推荐为首选的本地认证路径，并将“Anthropic API 密钥”推荐为首选的生产环境认证路径。此外，“Anthropic setup-token”作为一种受支持的令牌认证方式，依然可供选用。
2. 工作区 —— 代理文件的存放位置（默认为 `~/.openclaw/workspace`）。用于存放引导文件。
3. 网关 — 端口、绑定地址、认证模式、Tailscale 暴露设置。在交互式令牌模式下，可选择默认的明文令牌存储方式，或启用 SecretRef。非交互式令牌的 SecretRef 路径：`--gateway-token-ref-env <ENV_VAR>`。
4. 频道 —— 内置及捆绑的聊天频道，例如 BlueBubbles、Discord、飞书、Google Chat、Mattermost、Microsoft Teams、QQ 机器人、Signal、Slack、Telegram、WhatsApp 等。
5. Daemon —— 安装 LaunchAgent（macOS）、systemd 用户单元（Linux/WSL2），或原生 Windows 计划任务（并提供基于用户启动文件夹的备用方案）。如果令牌认证要求提供令牌，且 `gateway.auth.token` 由 SecretRef 管理，Daemon 安装过程会对其进行验证，但不会将解析出的令牌持久化存储到 Supervisor 服务的环境元数据中。如果令牌认证要求提供令牌，但配置的令牌 SecretRef 未能成功解析，Daemon 安装过程将被阻断，并提供相应的解决指引。如果同时配置了 `gateway.auth.token` 和 `gateway.auth.password`，且未设置 `gateway.auth.mode`，Daemon 安装过程将被阻断，直至明确设置该模式为止。
6. 健康检查 —— 启动网关并验证其正在运行。
7. 技能 — 安装推荐的技能及可选依赖项。

> 重新运行引导流程（onboarding）不会清除任何数据，除非您明确选择了“重置”（Reset）选项（或传递了 `--reset` 参数）。CLI 的 `--reset` 参数默认仅重置配置、凭据和会话；若需连同工作区一并重置，请使用 `--reset-scope full` 参数。如果当前配置无效或包含旧版键值，引导流程将提示您先运行 `openclaw doctor` 命令进行诊断。

远程模式仅配置本地客户端以连接至位于远端的网关，而不会在远程主机上安装或更改任何内容。

### 添加另一位代理
使用 `openclaw agents add <name>` 命令可创建一个独立的代理（Agent），该代理拥有专属的工作区、会话及认证配置文件。若运行命令时未指定 `--workspace` 参数，系统将自动启动引导配置流程。

该命令设置的配置项包括：
* `agents.list[].name`
* `agents.list[].workspace`
* `agents.list[].agentDir`

注意事项：
* 默认工作区路径为 `~/.openclaw/workspace-<agentId>`。
* 请添加绑定规则以路由入站消息（此操作也可在引导配置流程中完成）。
* 非交互模式参数：`--model`、`--agent-dir`、`--bind`、`--non-interactive`。

## 个人助理设置
OpenClaw 是一款自托管网关，能够将 Discord、Google Chat、iMessage、Matrix、Microsoft Teams、Signal、Slack、Telegram、WhatsApp、Zalo 等平台连接至 AI 代理。本指南将介绍“个人助理”模式的配置方法：即利用一个专用的 WhatsApp 号码，使其充当您全天候在线的 AI 助理。

### 安全第一
您正在赋予代理以下权限：
* 在您的机器上执行命令（具体取决于您的工具策略）
* 读取/写入您工作区内的文件
* 通过 WhatsApp、Telegram、Discord、Mattermost 以及其他内置渠道向外发送消息

建议采取保守策略：
* 务必配置 `channels.whatsapp.allowFrom` 参数（切勿在您的个人 Mac 上开启“对全网开放”的模式）。
* 为该助理专门配置一个专用的 WhatsApp 号码。
* “心跳检测”（Heartbeat）功能现已默认为每 30 分钟执行一次。在您完全信任当前配置之前，建议通过设置 `agents.defaults.heartbeat.every: "0m"` 来将其禁用。

### 先决条件
* 已安装并完成 OpenClaw 的初始设置。
* 一个用于助理的备用电话号码（SIM 卡、eSIM 或预付费卡）。

