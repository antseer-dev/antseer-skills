# antseer-skills

Web3 Skill 库 - 由 auto-skill-creator 工作流自动生成和维护。

## 目录结构

```
skills/
├── approved/      # A/B 级 Skill - 已发布
├── review/       # C 级 Skill - 待人工审核
├── evaluated/    # 已通过评估的 Skill
├── generated/    # 新生成的 Skill
└── rejected/     # 未通过审核的 Skill
```

## Skill 评级

| 评级 | 说明 | GitHub 推送 |
|------|------|-------------|
| A | 优质，直接发布 | ✅ |
| B | 良好，发布 | ✅ |
| C | 需人工审核 | ❌ 本地 |
| F | 不合格 | ❌ 本地 |

## 工作流

```
Demand Loader → Gap Detector → Creator → Evaluator → Tester → Publisher
```

## 贡献流程

1. 提交 Demand 文档到下游需求库
2. 工作流自动检测 Skill 缺口
3. 自动生成、评估、测试 Skill
4. 分级发布或人工审核

## 相关项目

- [auto-skill-creator](https://github.com/antseer-dev/auto-skill-creator) - Skill 生成工作流引擎
