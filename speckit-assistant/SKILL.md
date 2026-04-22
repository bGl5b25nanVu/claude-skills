---
name: speckit-assistant
description: |
  GitHub spec-kit 规格驱动开发助手。当用户想要：
  - 使用 spec-kit 或 specify-cli 工具
  - 进行规格驱动开发（Spec-Driven Development）
  - 初始化项目（specify init）
  - 使用 /speckit-* 系列 slash commands（/speckit-constitution、/speckit-specify、/speckit-plan、/speckit-tasks、/speckit-implement 等）
  - 创建功能规格文档
  - 生成技术实现计划
  - 管理项目开发流程
  必须激活此 skill，全程中文辅助用户完成 spec-kit 完整工作流程。
triggers:
  - spec-kit
  - specify-cli
  - 规格驱动开发
  - speckit
  - /speckit
  - 初始化项目
  - 创建规格
  - 技术规划
compatibility: |
  需要已安装 specify-cli：uv tool install specify-cli --from git+https://github.com/github/spec-kit.git
  需要在 spec-kit 项目目录中运行（包含 .specify/ 目录）
---

# Spec-Kit 规格驱动开发助手

全程辅助你完成 spec-kit 规格驱动开发的完整工作流程。

## 工作流程概览

```
1. /speckit-constitution  建立项目治理原则
2. /speckit-specify       创建功能规格（Spec）
3. /speckit-clarify       澄清模糊需求（可选但推荐）
4. /speckit-plan          创建技术实现计划
5. /speckit-checklist     生成质量检查清单（可选）
6. /speckit-tasks         生成可执行任务列表
7. /speckit-implement     执行实现
```

## 核心原则

1. **意图驱动** — 规格优先，关注"是什么"和"为什么"，而非技术栈
2. **多步骤迭代** — 逐步澄清和完善，而非一次性生成
3. **AI 协作** — 深度依赖 AI 模型能力，共同完成开发

---

## 第一步：项目初始化

如果项目尚未初始化，执行初始化：

```bash
# 持久安装 specify-cli
uv tool install specify-cli --from git+https://github.com/github/spec-kit.git

# 初始化项目（当前目录）
specify init --here --ai claude --ignore-agent-tools --force

# 检查工具完整性
specify check
```

**注意**：初始化后需要配置 git：
```bash
git config --global user.name "你的名字"
git config --global user.email "你的邮箱"
```

---

## 第二步：建立项目宪法（Constitution）

运行 `/speckit-constitution` 或手动编辑 `.specify/memory/constitution.md`

### 宪法模板

```markdown
# [项目名称] 宪法

## 核心原则

### I. 规格优先
- 每个功能从规格开始，先明确"做什么"和"为什么"
- 规格文档必须包含：功能描述、用户故事、验收标准
- 技术细节在规格澄清后确定

### II. 测试驱动
- 核心功能必须先写测试
- 测试必须覆盖：正常路径、边界条件、错误处理
- 测试覆盖率目标：核心逻辑 >= 80%

### III. 代码质量
- 遵循 SOLID 原则
- 函数不超过 50 行
- 关键逻辑必须有注释说明

### IV. 文档要求
- 每个公共 API 必须有文档字符串
- 复杂逻辑需要行内注释
- README 包含完整的运行说明

## 开发流程

1. 规格编写 → 2. 技术规划 → 3. 任务分解 → 4. 迭代实现 → 5. 测试验证

## 质量门槛

- 所有测试必须通过
- 代码必须通过 lint 检查
- 文档必须与实现同步更新

**版本**: 1.0.0 | **制定日期**: $(date +%Y-%m-%d)
```

---

## 第三步：创建功能规格（Specify）

运行 `/speckit-specify` 或创建 `.specify/memory/specs/[功能名].md`

### 规格文档结构

```markdown
# [功能名称] 规格

## 概述
[一句话描述功能的核心价值]

## 用户故事
作为 [角色]，我希望 [功能]，以便 [收益]。

## 功能详情

### 主要流程
1. [步骤 1]
2. [步骤 2]
3. [步骤 3]

### 边界情况
- [情况 1]：如何处理
- [情况 2]：如何处理

## 验收标准

- [ ] [标准 1]
- [ ] [标准 2]
- [ ] [标准 3]

## 不在范围内
- [明确排除的功能]

## 技术备注
[可选：已知的技术约束或决策]
```

### 规格编写技巧

**好的规格**：
- "用户输入有效的邮箱地址后，系统发送验证邮件"
- "当网络断开时，显示离线提示并缓存用户操作"

**差的规格**：
- "做一个邮箱功能"（太模糊）
- "使用 RabbitMQ 实现消息队列"（过早指定技术）

---

## 第四步：澄清需求（Clarify）

运行 `/speckit-clarify` 来识别和处理规格中的模糊之处。

### 常见澄清问题

| 问题类型 | 澄清问题示例 |
|---------|-------------|
| 输入验证 | 邮箱格式的具体要求是什么？最大长度？ |
| 错误处理 | API 超时时用户看到什么？重试几次？ |
| 边界条件 | 空列表如何显示？第一页/最后一页如何处理？ |
| 权限控制 | 哪些角色可以访问这个功能？ |
| 性能要求 | 最大响应时间是多少？并发用户数？ |

### 澄清记录模板

```markdown
## 澄清记录

| 问题 | 答案 | 日期 | 状态 |
|-----|------|------|------|
| [问题描述] | [回答] | YYYY-MM-DD | 已澄清 |
```

---

## 第五步：创建技术计划（Plan）

运行 `/speckit-plan` 或创建 `.specify/memory/plans/[功能名].md`

### 计划文档结构

```markdown
# [功能名称] 技术计划

## 概述
[功能简介和实施策略]

## 技术栈
- 前端：[技术选择及版本]
- 后端：[技术选择及版本]
- 数据库：[数据库选择]
- 部署：[部署方案]

## 系统架构

### 数据模型
```
[ER 图或数据模型描述]
```

### API 设计

| 端点 | 方法 | 描述 | 请求 | 响应 |
|------|------|------|------|------|
| /api/xxx | GET | 获取列表 | params | {data: []} |

## 实施步骤

### 阶段 1：基础设施
- [ ] 任务 1.1
- [ ] 任务 1.2

### 阶段 2：核心功能
- [ ] 任务 2.1
- [ ] 任务 2.2

### 阶段 3：集成测试
- [ ] 任务 3.1

## 风险与缓解

| 风险 | 影响 | 缓解措施 |
|------|------|----------|
| [风险描述] | [影响程度] | [缓解方案] |

## 里程碑

- M1：完成基础设施（日期）
- M2：核心功能完成（日期）
- M3：测试完成（日期）
```

---

## 第六步：生成任务列表（Tasks）

运行 `/speckit-tasks` 或手动创建 `.specify/memory/tasks/[功能名].md`

### 任务格式

```markdown
# [功能名称] 任务列表

## 元数据
- 功能：[功能名称]
- 创建日期：[日期]
- 状态：待开始

## 任务列表

### 前置任务
- [ ] PRE-001: [任务描述] (依赖: 无)
- [ ] PRE-002: [任务描述] (依赖: PRE-001)

### 核心任务
- [ ] CORE-001: [任务描述] (依赖: PRE-002)
- [ ] CORE-002: [任务描述] (依赖: CORE-001)

### 后续任务
- [ ] POST-001: [任务描述] (依赖: CORE-002)

## 任务详情

### PRE-001: [任务名称]
- **描述**：[详细描述]
- **验收标准**：[完成条件]
- **预计工时**：X 小时
- **实际工时**：[留空]
- **备注**：[备注]
```

### 任务标记

| 标记 | 含义 |
|------|------|
| `[P]` | 可并行执行 |
| `[B]` | 阻塞任务，必须先完成 |
| `[T]` | 需要测试 |

---

## 第七步：执行实现（Implement）

运行 `/speckit-implement` 或按任务列表顺序执行。

### 实现指南

1. **按依赖顺序执行**
   - 先完成前置任务
   - 核心任务通常可并行（标记 `[P]`）

2. **TDD 方法（如适用）**
   - 编写测试 → 运行测试（失败）→ 编写代码 → 运行测试（通过）→ 重构

3. **提交代码**
   ```bash
   # 创建功能分支
   git checkout -b feature/[功能名]

   # 提交（使用 conventional commits）
   git commit -m "feat([功能]): [描述]"
   ```

4. **验证实现**
   - 运行所有测试
   - 检查代码格式
   - 验证文档更新

---

## 常用命令参考

```bash
# 安装/更新 specify-cli
uv tool install specify-cli --from git+https://github.com/github/spec-kit.git

# 检查环境
specify check

# 初始化项目
specify init --here --ai claude --ignore-agent-tools --force

# 列出可用扩展
specify extension list

# 列出可用预设
specify preset list

# 版本信息
specify version
```

---

## 文件结构参考

```
项目/
├── .specify/
│   ├── memory/
│   │   ├── constitution.md     # 项目宪法
│   │   ├── specs/              # 功能规格
│   │   ├── plans/              # 技术计划
│   │   └── tasks/              # 任务列表
│   ├── templates/              # 模板文件
│   ├── workflows/              # 工作流脚本
│   └── extensions.yml         # 扩展配置
├── .claude/
│   └── skills/                # Claude skills
└── [项目文件]
```

---

## 故障排除

### 问题：specify init 失败
**解决方案**：
```bash
# 设置 git 用户信息
git config --global user.name "Your Name"
git config --global user.email "your@email.com"

# 或使用 --no-git 跳过 git 初始化
specify init --here --ai claude --ignore-agent-tools --no-git
```

### 问题：slash command 不生效
**解决方案**：确保在 spec-kit 项目目录中运行，且 .specify/ 目录存在。

### 问题：权限错误
**解决方案**：
```bash
chmod +x .specify/scripts/*.sh
```

---

## 下一步

完成此流程后，你可以：

1. **迭代开发** — 使用 `/speckit-specify` 开始新功能
2. **代码审查** — 运行 `/speckit-analyze` 进行一致性分析
3. **团队协作** — 配置扩展实现 Jira/GitHub Issues 同步

有问题随时问我！
