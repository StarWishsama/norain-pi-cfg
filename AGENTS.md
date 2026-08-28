## 环境信息

- **语言**: 所有输出（包括思考过程、回复、代码注释和 commit 信息）一律使用简体中文
- **操作系统**: Windows 11 | **AI 终端**:PowerShell | **用户终端**: PowerShell
- **环境限制**: 无 Python 环境，避免使用 Python 相关命令 和 脚本
- **已安装 CLI**: GitHub CLI（`gh`），涉及 GitHub 仓库操作时优先使用

## 编码规则

1. **不要**做过多防御性编程、测试点到即止、最小化完成目标
2. **禁止** 在实现需求时使用第三方依赖直接尝试逆向/反编译依赖，而是使用 context7 查看文档。除非用户明确要求了需要反编译以排查问题。
3. 需要查找代码间的关系时，优先使用 `codegraph` MCP。
3. **禁止** 编写 node 或 python 脚本以进行快捷的多步/复杂操作，除非用户明确要求编写 或 你是 PTC Mode。
4. 所有新增的代码片段优先加在尾部，不要影响 git merge。
5. 若当前项目为 Java/Kotlin 语言，执行构建操作/检查代码错误时优先使用 Jetbrains Tool，其他语言则不使用。

## 命令执行策略

存在权限系统管理你可使用的命令，除了以下可直接使用的命令之外，请你一条一条执行命令，不要让用户同时审批多条命令执行，请积极采纳系统返回的 `deny` 中包含的拒绝原因。

### 允许直接使用的命令

- **文件操作**: 使用专用工具 (Read, Write, Edit, ffgrep, fffind, fff-multi-grep)，不使用 find/grep/cat/echo 等 shell 命令
- **Git 只读操作**: `git status/log/diff/branch/show/blame`

### 不允许的行为

- 在非 PTC Mode 下，让用户执行长串代码块。
- 需要交互式操作、长时间运行的命令。
- 需要管理员权限的命令。（需要输出代码块让用户自行决定是否执行）

## MCP 工具

首次使用某 MCP 服务器时需先 `connect`。

### 使用方式

- 查看服务器状态：`mcp({})`
- 连接服务器：`mcp({ connect: "server-name" })`
- 搜索工具：`mcp({ search: "keyword" })`
- 查看工具详情：`mcp({ describe: "tool_name" })`
- 调用工具：`mcp({ tool: "tool_name", args: { ... } })`
- 批量调用：用 `mcpScript` 编写 JavaScript 串联多个调用

## 第三方库/框架文档查询

当用户询问关于库（library）、框架、SDK、API、CLI 工具或云服务的问题时（即使是 React、Next.js、Prisma、Express、Tailwind、Django 或 Spring Boot 等知名库），请使用 Context7（`resolve-library-id` / `query-docs` 工具或 `ctx7` CLI）来获取最新文档。其中包括了 API 语法、配置、版本迁移、特定于库的调试、安装指引以及 CLI 工具的使用。即使你认为自己知道答案也请使用——你的训练数据可能没有包含最新的变更。在查询库文档时，优先使用此方式而非网页搜索。

不需要使用的场景：重构、从头编写脚本、业务逻辑调试、代码审查或通用编程概念。

### 步骤

1. 解析库：使用 `resolve-library-id` 工具（或 `npx ctx7@latest library <name> "<用户的提问>"`）——使用包含正确标点符号的官方库名称（例如 "Next.js" 而非 "nextjs"，"Customer.io" 而非 "customerio"，"Three.js" 而非 "threejs"）。
2. 选择最佳匹配项（ID 格式：`/org/project`），参考标准：完全匹配的名称、描述的相关性、代码片段数量、来源声誉（优先选择 High/Medium）以及基准得分（越高越好）。如果结果看起来不正确，请尝试备用名称或查询词（例如使用 "next.js" 而非 "nextjs"，或重新表述问题）。
3. 获取文档：使用 `query-docs` 工具（或 `npx ctx7@latest docs <libraryId> "<用户的提问>"`）。
4. 结合获取到的文档进行回答。

除非用户直接提供了 `/org/project` 格式的 ID，否则你**必须**先调用 `resolve-library-id`（或 `library`）以获取有效的 ID。使用用户的完整问题作为查询内容——具体详尽的查询会比模糊的单个单词返回更好的结果。每个问题执行的工具调用/命令不要超过 3 次。切勿在查询中包含敏感信息（API 密钥、密码、凭据等）。

如需特定版本的文档，请使用 `resolve-library-id` 输出中的 `/org/project/version`（例如 `/vercel/next.js/v14.3.0`）。

如果 Context7 出现配额错误（quota error），请告知用户并建议其设置 `CONTEXT7_API_KEY` 环境变量以获得更高使用额度。**不要**在未通知用户的情况下静默回退到训练数据进行回答。