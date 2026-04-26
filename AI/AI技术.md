当前主流 AI 技术可以大致分成几个层面来看：**模型（大脑）**、**产品（应用）**、以及**开发工具/生态（用来构建AI的工具）**。如ChatGPT、DeepSeek、Claude、Claude Code，以及 OpenClaw基本都分布在这些层级中。

# 核心：大模型（LLM）

大语言模型（Large Language Model），这是所有AI系统的“引擎”。

## 代表模型厂商

- OpenAI → GPT系列（如 GPT-4 / GPT-5）
- Anthropic → Claude系列，编程与应用开发领域的佼佼者。
- DeepSeek → DeepSeek-V3 / R1（推理模型）
- Google DeepMind → Gemini
- Meta → LLaMA（开源倾向）

# AI产品（能直接使用的）

这些是“包装好的AI”。

## 聊天/通用助手

- ChatGPT（基于GPT）
- Claude（基于Claude模型）
- Gemini（基于Gemini）

关系：

- 本质是**不同公司用自家模型做的应用**

# 开发工具（AI写代码 / Agent）

这类AI不再满足于“对话”，而是主动走向“执行”，致力于将大模型的能力转化为真实的行动。**Claude Code** 和 **OpenClaw** 就在这一层。

## OpenClaw

万能数字员工与AI操作系统。最大的优势在于其**强大的任务执行和系统集成能力**，能直接操作你的电脑，如读取文件、操作浏览器、收发邮件、运行脚本。

**它与大语言模型的关系**：OpenClaw本身是“执行层”而非“智力层”。它必须调用外部LLM（如ChatGPT、DeepSeek）作为其推理决策的核心。它更像一个“模型路由器”或“网关”，可以灵活地选择最适合每项任务的模型来执行。

## AI编程工具

- Claude Code（基于Claude模型的开发工具）：这是Anthropic为自家Claude模型打造的**编程专家**，专门在命令行里帮助开发者理解项目、生成代码、重构、调试、审查等，与OpenClaw的全能定位形成补充。
- GitHub Copilot（基于GPT/Claude等）。
- Cursor（AI IDE）：一款AI驱动的代码编辑器，将AI能力深度集成到开发流程中，是目前最实用的编程工具之一。

特点：

- 面向开发者
- 可以：
    - 自动写代码
    - 修改项目
    - 运行命令（Agent能力）

# OpenAI API Key
## OpenAI API Key 与 ChatGPT

申请OpenAI API Key，本质上就是开启一段按量付费的旅程。关键在于，你需要把它和日常用的ChatGPT网页版区分开——支付ChatGPT Plus的费用并不会自动让你获得API的调用权限。OpenAI API的访问权限和ChatGPT的订阅是**完全独立**的两套系统。

一个更通俗的比喻是：**API Key就像是你的“水表”**，而ChatGPT Plus订阅类似于你买的“瓶装水”。

- **API Key（水表）**：需要你先往账户里**充值**（预付费），然后每用一吨水（Token），就扣一次钱。它本身不包含任何免费水量。
- **ChatGPT Plus（瓶装水）**：你每个月付固定费用，拿到的是一瓶容量固定的水，用不完也不能退款。

## 注册账号与生成Key

1. **访问官网并注册**：前往 [platform.openai.com](https://platform.openai.com/)，用邮箱、Google或Microsoft账号注册。注意，这一步可能需要稳定的网络环境。
2. **验证必要信息**：按要求验证邮箱和手机号。其中，**海外手机号验证**是许多人遇到的第一个门槛。
3. **创建API Key**：登录后，在左侧导航栏找到 **API Keys**，点击 **Create new secret key**。给你的Key起个名字（比如“MyFirstApp”），然后点击创建。
4. **立即保存Key**：这是最重要的一步！系统会显示一串以 `sk-proj-` 开头的密钥，**请务必立即复制并保存到安全的地方**。一旦关闭页面，你就再也看不到了。

## 完成计费绑定

1. **进入Billing页面**：在左侧导航栏找到并进入 **Billing**（或Settings → Billing）。
2. **添加支付方式**：点击 **Payment methods** 添加支付方式。这里的关键是，你需要一张**国际信用卡（Visa/Mastercard）。对于国内开发者，普通的银联卡通常无效，可以考虑：
    - **助力海外朋友**：这是最直接的方法。
    - **使用虚拟信用卡**：市面上一些虚拟卡服务（如Depay等）相当于一个“中间人”，你往里充值后，它就可以像国际信用卡一样使用了。
3. **进行首次充值**：OpenAI采用**预付费（Pre-paid Credit）模式。你需要先充值才能使用API。**  **最低充值额为$5**。目前新用户注册通常会赠送 **$5的信用额度**，但请注意它可能有**3个月的有效期。
4. **设置使用限额**：为避免因程序Bug或意外导致费用超额，建议在 **Usage limits** 页面设置一个每月消费上限。这是一个很好的省钱技巧。

## 计费方式

OpenAI API就像水电一样，用多少，付多少（Pay-as-you-go），核心计费单位是 **Token**。

- **Token是什么？**
    - 你可以理解为一种“字数费”，它是API处理文本的最小单位。
    - 大致来说，1个Token约等于0.75个英文单词，或半个中文字符。也就是说，输入一个汉字大约需要2个Token。
    - 费用由**输入Token**（你的问题）和**输出Token**（AI的回答）两部分构成，其中**输出Token的单价通常是输入Token的4-6倍。
