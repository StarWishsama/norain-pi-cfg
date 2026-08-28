# norain-pi-cfg

个人使用的 Pi 配置，主要包含了 UI 优化、子代理、用量查询的插件。

## 配置文件

- `settings.json`：默认模型、工具、Pi 包和界面设置
- `mcp.json`：MCP 服务配置
- `pi-lsp.json`：TypeScript、Java 和 Vue 的 LSP 配置
- `extensions/`：本地扩展配置
- `AGENTS.md`：工作约定与编码规则

## 扩展

### 核心能力

- `@gotgenes/pi-permission-system`：权限控制、路径访问规则和操作确认
- `@gotgenes/pi-subagents`：子代理
- `@juicesharp/rpiv-ask-user-question`：向用户发起结构化问题
- `pi-mcp-adapter`：接入 MCP 工具服务
- `pi-nano-context`：上下文管理
- `@ff-labs/pi-fff`：文件查找和内容搜索
- `@upstash/context7-pi`：查询库和框架文档
- `cc-safety-net`：操作安全防护

### 终端与交互体验

- `pi-tool-display`：优化工具、搜索、MCP、Shell 和差异输出的展示
- `pi-animations`：为工作、思考和工具调用提供终端动画
- `@99percentpeople/pi-thinking-fold`：折叠思考内容
- `pi-image-paste`：支持在会话中粘贴图片
- `pi-diff`：提供语法高亮、分栏和统一格式的差异展示
- `ayghri/i-have-adhd`：让输出更直接、步骤更清晰，减少冗余内容

### 上下文、性能与使用统计

- `@lll9p/pi-better-compaction`：支持 Openai 原生压缩的上下文压缩增强插件
- `pi-rtk-optimizer`：整理和压缩命令输出，减少上下文占用
- `pi-tps`：显示模型 tps, ttft 等信息
- `pi-turing-usage`：统计和展示使用量
- `pi-wakatime`：记录编码活动

### 模型与个性化扩展

- `pi-antigravity`：Antigravity 模型提供商支持
- [pi-norain-extension](https://github.com/StarWishsama/pi-norain-extension): 修改了启动 header
- `@juicesharp/rpiv-warp`：Warp Terminal 辅助插件
- `@ogulcancelik/pi-herdr`：Herdr 辅助插件

## 配套服务

- MCP：Arthas、IntelliJ IDEA、DBX 和 CodeGraph
- LSP：TypeScript、Java 和 Vue
