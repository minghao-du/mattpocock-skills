# 效率 (Productivity)

通用工作流工具，非针对代码。

## 用户触发 (User-invoked)

仅在用户显式调用时触发（Claude Code: `disable-model-invocation: true`；Codex: `policy.allow_implicit_invocation: false` 在 `agents/openai.yaml` 中）。

- **[grill-me](./grill-me/SKILL.md)**: 通过提问打磨计划或设计，直到设计树的每个分支都被解决。

## 模型触发 (Model-invoked)

模型或用户可触达（丰富的触发词短语以便模型调用）。

- **[grilling](./grilling/SKILL.md)**: 就计划、决策或想法对用户进行持续提问，直到设计树的每个分支都被解决。
