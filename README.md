# claude-skills

Claude Code 自定义技能仓库，提供多种开发辅助功能。

## 包含的 Skills

### speckit-assistant

GitHub spec-kit 规格驱动开发中文全流程助手，覆盖：

- 项目初始化（specify init）
- 宪法（Constitution）编写
- 功能规格（Spec）创建
- 需求澄清（Clarify）
- 技术计划（Plan）制定
- 任务列表（Tasks）生成
- 实现执行（Implement）

## 安装

```bash
# 克隆仓库
git clone https://github.com/bGl5b25nanVu/claude-skills.git

# 复制 skill 到项目
cp -r <skill-name> /path/to/your-project/.claude/skills/
```

## 快速开始（spec-kit）

1. **安装 spec-kit**
   ```bash
   uv tool install specify-cli --from git+https://github.com/github/spec-kit.git
   ```

2. **初始化项目**
   ```bash
   specify init --here --ai claude --ignore-agent-tools --force
   ```

3. **开始开发流程**
   - `/speckit-constitution` — 建立项目原则
   - `/speckit-specify` — 创建功能规格
   - `/speckit-clarify` — 澄清模糊需求
   - `/speckit-plan` — 创建技术计划
   - `/speckit-tasks` — 生成任务列表
   - `/speckit-implement` — 执行实现

## 文档

详见各 skill 目录下的 SKILL.md

## 许可证

MIT
