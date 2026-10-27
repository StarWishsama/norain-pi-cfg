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
- 文件查找和内容搜索使用 Pi 内置的 `find`、`grep`、`ls` 工具
- `@upstash/context7-pi`：查询库和框架文档
- `pi-web-access`：网页搜索与内容读取
- `deword`：读取和编辑 Word 文档

### 终端与交互体验

- `pi-hashline-edit-pro`：通过行锚点读取和编辑文件
- `pi-animations`：为工作、思考和工具调用提供终端动画
- `@99percentpeople/pi-thinking-fold`：折叠思考内容
- `pi-image-paste`：支持在会话中粘贴图片
- `pi-diff`：提供语法高亮、分栏和统一格式的差异展示
- `ayghri/i-have-adhd`：让输出更直接、步骤更清晰，减少冗余内容

### 上下文、性能与使用统计

- `@narumitw/pi-codex-compact`：Codex 上下文压缩
- `pi-rtk-optimizer`：整理和压缩命令输出，减少上下文占用
- `pi-tps`：显示模型 tps, ttft 等信息
- `pi-wakatime`：记录编码活动

### 模型与个性化扩展

- [pi-turing-usage](https://github.com/StarWishsama/pi-turing-usage)：查询模型用量
- [pi-norain-extension](https://github.com/StarWishsama/pi-norain-extension): 修改了启动 header
- `@juicesharp/rpiv-warp`：Warp Terminal 辅助插件
- `@narumitw/pi-herdr`：Herdr 辅助插件

## 配套服务

- MCP：Arthas、IntelliJ IDEA、DBX 和 CodeGraph
- LSP：TypeScript、Java 和 Vue

## 同步约定

从本机 `~/.pi/agent` 同步可公开的配置，保留仓库的默认模型和可移植 MCP/LSP 命令；不复制凭据、私有模型配置、本机代理和运行数据。

`extensions/pi-better-compaction/` 和 `extensions/pi-tool-display/` 保留已有配置，当前包列表未启用对应扩展。
