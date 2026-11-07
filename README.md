# WorkRoom

> 一个跨 agent 共享的 AI 技能库备份仓库。
>
> 收录 **27 个** 精选 Agent Skills，按「智能体开发」与「办公效率」两组预设备份，一键同步到 Claude Code、Codex 等 56 种编码代理。

---

## 这是什么

`WorkRoom` 不是普通的代码仓库，而是 [Skills Manager](https://github.com/xingkongliang/skills-manager) 的 **Git 备份库**。

它做的事情很简单：把你的 **AI 技能（Agent Skills）集中到一处管理**，再分发到各个 AI 编程工具里。

一次维护，多处可用：

- 技能只装一份，Claude Code、Codex、Cursor、Gemini CLI 共享同一个库
- 换机器、重装系统，`git pull` 就能恢复全部技能
- 技能带来源元数据，可追踪上游更新
- 按预设分组，不同项目开不同的技能组合，互不干扰

---

## 目录结构

```
WorkRoom/
├── .skills-manager/          # 元数据（由 CLI 自动维护）
│   ├── protocol.json         # 备份协议版本
│   ├── schema.json           # 结构声明
│   ├── skills/               # 每个技能一份 JSON（来源/标签/预设）
│   └── scenarios/            # 预设（旧版称 scenario）定义
├── .gitignore
├── docx/                     # ↓ 每个技能一个目录
│   ├── SKILL.md              #   技能指令主体
│   └── scripts/              #   可选的辅助脚本
├── xlsx/
├── pptx/
├── pdf/
└── ...                       # 共 27 个技能目录
```

**两层结构，缺一不可：**

| 层 | 位置 | 作用 |
|---|---|---|
| 文件层 | `<skill>/SKILL.md` | 真正被 agent 读取的技能内容 |
| 元数据层 | `.skills-manager/skills/<uuid>.json` | 记录来源、标签、预设归属 |

> ⚠️ 只放目录不写元数据，技能能跑但会失去更新追踪；只写元数据没有目录，技能会加载失败。**务必用 CLI 写入，不要手改。**

---

## 技能清单

### 一、智能体开发（13 个）

覆盖从方案规划、编码、调试到质量把关、MCP 扩展的完整开发链路。

| 技能 | 用途 | 来源 |
|---|---|---|
| `using-superpowers` | 工程方法论主线，串联完整开发流程 | [obra/superpowers](https://github.com/obra/superpowers) |
| `wayfinder` | 复杂任务的路径规划与拆解 | [mattpocock/skills](https://github.com/mattpocock/skills) |
| `grill-me` | 连环追问，压力测试方案漏洞 | [mattpocock/skills](https://github.com/mattpocock/skills) |
| `systematic-debugging` | 系统化排障，避免瞎试 | [obra/superpowers](https://github.com/obra/superpowers) |
| `test-driven-development` | TDD 工作流 | [obra/superpowers](https://github.com/obra/superpowers) |
| `code-review` | 代码评审，抓真问题 | [mattpocock/skills](https://github.com/mattpocock/skills) |
| `verification-before-completion` | 交付前强制自检，杜绝"看起来对" | [obra/superpowers](https://github.com/obra/superpowers) |
| `mcp-builder` | 开发 MCP 服务器，接入外部 API | [anthropics/skills](https://github.com/anthropics/skills) |
| `deep-agents-memory` | 长期记忆与上下文管理 | [langchain-ai/langchain-skills](https://github.com/langchain-ai/langchain-skills) |
| `skill-creator` | 设计并生成自己的技能 | [anthropics/skills](https://github.com/anthropics/skills) |
| `ui-ux-pro-max` | UI/UX 设计智能，多端规范 | [nextlevelbuilder](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) |
| `find-skills` | 按需求发现可用技能 | [vercel-labs/skills](https://github.com/vercel-labs/skills) |
| `manage-skills` | 技能库自身的增删改查 | [skills-manager](https://github.com/xingkongliang/skills-manager) |

### 二、办公效率（14 个）

文档产出、写作润色、信息调研，外加 **4 个降低 token 消耗** 的技能。

| 技能 | 用途 | 来源 |
|---|---|---|
| `docx` | 创建/编辑 Word 文档与模板 | [anthropics/skills](https://github.com/anthropics/skills) |
| `xlsx` | Excel 表格读写与公式 | [anthropics/skills](https://github.com/anthropics/skills) |
| `pptx` | 生成与修改演示文稿 | [anthropics/skills](https://github.com/anthropics/skills) |
| `pdf` | PDF 解析、填写、转换 | [anthropics/skills](https://github.com/anthropics/skills) |
| `canvas-design` | 版式、海报、视觉稿设计 | [anthropics/skills](https://github.com/anthropics/skills) |
| `brand-guidelines` | 统一品牌视觉与文案规范 | [anthropics/skills](https://github.com/anthropics/skills) |
| `email-drafter` | 邮件起草与语气调整 | [claude-office-skills](https://github.com/claude-office-skills/skills) |
| `humanizer` | 去除 AI 写作痕迹，更像人写的 | [blader/humanizer](https://github.com/blader/humanizer) |
| `last30days` | 近 30 天全网趋势调研 | [mvanhorn](https://github.com/mvanhorn/last30days-skill) |
| `office-productivity` | 办公流程总编排 | [agentic-awesome-skills](https://github.com/sickn33/agentic-awesome-skills) |
| `i-have-adhd` | **结论前置，砍掉冗长铺垫** | [ayghri](https://github.com/ayghri/i-have-adhd) |
| `principle-guard-the-context-window` | **上下文窗口守卫，防越界** | [cursor/plugins](https://github.com/cursor/plugins) |
| `cost-aware-llm-pipeline` | **成本感知的模型调用链** | [affaan-m/ecc](https://github.com/affaan-m/ecc) |
| `llm-caching` | **提示词缓存复用，降本** | [devops-security-agent-skills](https://github.com/bagelhole/devops-security-agent-skills) |

---

## 降本组合（重点）

> 四个技能配合使用，是这套库里投入产出比最高的一组。粗体为降本主力。

| 环节 | 技能 | 省在哪 |
|---|---|---|
| 输出端 | **`i-have-adhd`** | 结论前置、压缩铺垫，单次回复显著变短 |
| 输入端 | **`principle-guard-the-context-window`** | 阻止无节制读文件，守住上下文窗口 |
| 调用层 | **`llm-caching`** | 重复前缀命中缓存，按缓存价计费 |
| 链路层 | **`cost-aware-llm-pipeline`** | 按任务难度选模型，简单活不烧贵模型 |
| 流程层 | `systematic-debugging` | 少走弯路 = 少烧 token |
| 流程层 | `verification-before-completion` | 一次做对，避免返工重跑 |

**建议四个全开。** 单用 `i-have-adhd` 只能省输出，配合另外三个才能覆盖输入、调用、链路三层。

---

## 前置要求

| 项目 | 说明 |
|---|---|
| Skills Manager | 桌面版 ≥ 2.0.0，或 `skills-manager-cli` ≥ 1.43 |
| Git | 已安装并配置好凭据 |
| 目标 agent | Claude Code / Codex 等，任一已安装即可 |

支持的 agent 共 **56 种**（Claude Code、Codex、Cursor、GitHub Copilot、Gemini CLI、OpenCode、Windsurf、Cline、TRAE、Qwen Code…），Skills Manager 会自动检测本机装了哪些。

---

## 使用方式

### 首次恢复到本机

```bash
# 1. 克隆仓库
git clone https://github.com/huang030228/WorkRoom.git

# 2. 用 Skills Manager 指向该目录作为备份库
#    推荐：打开桌面版 → 设置 → Git 备份 → 选择此目录并拉取

# 3. 确认技能已入库
skills-manager-cli --json skills list
```

### 部署到指定 agent

```bash
# 单个技能
skills-manager-cli skills deploy docx --agent claude_code

# 整组预设（推荐）
skills-manager-cli presets deploy "智能体开发" --agent claude_code --agent codex
```

### 日常维护

```bash
# 检查上游是否有更新（只探测，不改文件）
skills-manager-cli skills check --all

# 应用全部更新
skills-manager-cli skills update --all

# 看到变更后提交并推送
skills-manager-cli git commit --message "chore: 同步上游更新"
skills-manager-cli git push
```

---

## 常用命令速查

| 目的 | 命令 |
|---|---|
| 看库里有什么 | `skills-manager-cli --json skills list` |
| 搜索新技能 | `skills-manager-cli --json skills search "关键词" --limit 5` |
| 安装技能 | `skills-manager-cli skills install <owner>/<repo>/<skill>` |
| 部署到 agent | `skills-manager-cli skills deploy <skill> --agent <key>` |
| 取消部署 | `skills-manager-cli skills undeploy <skill> --agent <key>` |
| 按标签筛选 | `skills-manager-cli --json skills list --tag cost` |
| 看预设 | `skills-manager-cli --json presets list` |
| 查看本机 agent | `skills-manager-cli --json agents list` |
| 备份状态 | `skills-manager-cli --json git status` |

> CLI 路径因平台而异：Windows 为 `%USERPROFILE%\.skills-manager\bin\skills-manager-cli.exe`，macOS/Linux 为 `~/.skills-manager/bin/skills-manager-cli`。

---

## 注意事项

**不要手改元数据。** `.skills-manager/` 下的 JSON 由 CLI 维护，手改会导致库状态不一致，甚至让技能失联。

**不要删除技能目录里的文件。** `skills update` 会整体替换技能目录，本地改过的内容可能被覆盖。要定制请复制成新技能。

**部署 ≠ 安装。** 安装只是进库，技能对 agent 还不可见；必须 `deploy` 才会真正落到 agent 的技能目录。

**换机器时先 pull 再操作。** 避免本地旧状态覆盖远端。

---

## 已知限制

- **代理环境**：本机 HTTP 代理会拦截 `github.com:443` 的 git 协议（返回 502），但 `codeload.github.com` 可达。若 `skills install` 报 clone 超时，可改用 tarball 下载后 `skills adopt --git-url ...` 登记。
- **大仓库易超时**：`anthropics/skills` 体积较大，直接 install 可能超时，建议用上述 tarball 方式。
- **安装中断留孤儿目录**：进程被强杀会留下"有 `SKILL.md` 但无元数据"的目录，表现为仓库里有文件夹但 `skills list` 里没有。需重新 `skills adopt` 登记。

---

## 参考

- [Skills Manager](https://github.com/xingkongliang/skills-manager) — 技能库管理工具
- [Agent Skills 规范](https://github.com/anthropics/skills) — 官方技能标准
- [skills.sh](https://skills.sh) — 技能市场，可查安装量

---

<sub>本仓库由 Skills Manager 自动备份维护。技能版权归各原作者所有，详见各技能目录内的 LICENSE。</sub>