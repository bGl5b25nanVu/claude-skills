# speckit-skills

Claude Code skills for GitHub spec-kit 规格驱动开发工作流

## 包含的 Skills

### speckit-assistant

中文全流程辅助的 spec-kit 开发助手，覆盖：

- 项目初始化
- 宪法（Constitution）编写
- 功能规格（Spec）创建
- 需求澄清（Clarify）
- 技术计划（Plan）制定
- 任务列表（Tasks）生成
- 实现执行（Implement）

## 安装

```bash
# 克隆仓库
git clone https://github.com/bGl5b25nanVu/speckit-skills.git

# 复制 skill 到项目
cp -r speckit-assistant /path/to/your-project/.claude/skills/
```

## 快速开始

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

详见 [speckit-assistant/SKILL.md](speckit-assistant/SKILL.md)

## 许可证

MIT
