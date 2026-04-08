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
![工作原理图](工作原理图.png)
Gateway 网关是会话、路由和渠道连接的唯一事实来源。

## 功能
### 亮点
![关键能力](关键能力.png)

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