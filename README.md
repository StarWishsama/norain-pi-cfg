# Pi 配置

这是一个可公开分享的 Pi 用户级配置仓库，整理自本机 `~/.pi/agent`。

## 内容

- `settings.json`：默认模型、工具、Pi 包和界面设置
- `mcp.json`：MCP 服务配置
- `pi-lsp.json`：LSP 服务配置（命令按 PATH 查找）
- `extensions/`：本地扩展及扩展配置
- `AGENTS.md`：全局工作约定

`auth.json`、`models.json`、会话记录、缓存、日志和本机运行状态不纳入仓库。

## 使用

在 PowerShell 中临时使用这份配置：

```powershell
$env:PI_CODING_AGENT_DIR = "$HOME\.pi\git"
pi
```

首次使用时，通过 `/login` 或环境变量配置模型认证，并按需安装配置中的 Pi 包：

```text
pi install npm:<package>
```

LSP 配置中的命令需要提前安装并加入 PATH；MCP 配置中的本地服务按实际环境启用。

## 安全说明

Pi 扩展拥有当前用户的本机权限。公开或安装前请审查扩展源码；不要提交 API 密钥、OAuth 凭据、私有服务地址或会话内容。
