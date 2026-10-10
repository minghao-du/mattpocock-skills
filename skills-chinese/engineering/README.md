# 工程 (Engineering)

日常代码工作所使用的技能。

## 用户触发 (User-invoked)

仅在用户显式调用时触发（Claude Code: `disable-model-invocation: true`；Codex: `policy.allow_implicit_invocation: false` 在 `agents/openai.yaml` 中）。

- **[grill-with-docs](./grill-with-docs/SKILL.md)**: 质询会话，同时构建项目的领域模型，提炼术语并直接更新 `GLOSSARY.md` 和 ADR。

## 模型触发 (Model-invoked)

模型或用户可触达（丰富的触发词短语以便模型调用）。

- **[domain-modeling](./domain-modeling/SKILL.md)**: 通过质疑术语、结合场景进行压力测试并就地更新 `GLOSSARY.md` 与 ADR，积极构建并提炼项目的领域模型。
