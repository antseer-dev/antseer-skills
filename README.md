# antseer-skills

Web3 Skill 库 - 由 auto-skill-creator 工作流生成并通过审查的 Skill 集合。

## 目录结构

```
skills/
├── {skill_id}/
│   ├── SKILL.md        # Skill 定义
│   ├── scripts/        # 相关脚本
│   └── ...
├── {skill_id}/
│   └── ...
```

每个 Skill 独立目录，包含完整的 Skill 定义和执行脚本。

## 贡献流程

1. 提交 Demand 文档到下游需求库
2. 工作流自动检测 Skill 缺口
3. 自动生成、评估、测试 Skill
4. 通过审查后自动发布到此仓库

## 相关项目

- [auto-skill-creator](https://github.com/antseer-dev/auto-skill-creator) - Skill 生成工作流引擎
