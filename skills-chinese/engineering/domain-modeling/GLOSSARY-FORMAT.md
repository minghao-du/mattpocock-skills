# GLOSSARY.md 格式

## 结构

```md
# {上下文名称}

{用一两句话描述该上下文是什么以及它为何存在。}

## 语言

**Order**:
{用一两句话描述该术语}
_Avoid_: Purchase, transaction

**Invoice**:
交货后发送给客户的付款请求。
_Avoid_: Bill, payment request

**Customer**:
下订单的个人或组织。
_Avoid_: Client, buyer, account
```

## 规则

- **有鲜明主见。** 当同一个概念存在多个词汇时，选择最合适的一个，并将其余词汇列在 `_Avoid_` 下。
- **定义保持紧凑。** 最多一到两句话。定义它“是什么”，而不是它“做什么”。
- **仅包含特定于该项目上下文的术语。** 通用编程概念（超时、错误类型、实用工具模式）不属于此类，即使项目中大量使用也不应包含。添加术语前先自问：这是该上下文特有的概念，还是通用编程概念？只有前者才属于这里。
- **在出现自然聚合时按二级标题对术语分组。** 如果所有术语属于单一且内聚的领域，扁平列表即可。

## 单上下文与多上下文代码库

**单上下文（大多数代码库）：** 代码库根目录下有一个 `GLOSSARY.md`。

**多上下文：** 代码库根目录下的 `GLOSSARY-MAP.md` 列出了各个上下文、它们所在的位置以及它们彼此之间的关系：

```md
# Glossary Map

## Contexts

- [Ordering](./src/ordering/GLOSSARY.md): 接收并跟踪客户订单
- [Billing](./src/billing/GLOSSARY.md): 生成发票并处理付款
- [Fulfillment](./src/fulfillment/GLOSSARY.md): 管理仓库拣货与发货

## Relationships

- **Ordering → Fulfillment**: Ordering 发出 `OrderPlaced` 事件；Fulfillment 消费该事件以开始拣货
- **Fulfillment → Billing**: Fulfillment 发出 `ShipmentDispatched` 事件；Billing 消费该事件以生成发票
- **Ordering ↔ Billing**: 共享 `CustomerId` 和 `Money` 类型
```

技能会推断适用哪种结构：

- 如果存在 `GLOSSARY-MAP.md`，读取它以查找上下文
- 如果仅存在根目录下的 `GLOSSARY.md`，则为单上下文
- 如果两者均不存在，在确定第一个术语时延迟创建根目录 `GLOSSARY.md`

当存在多个上下文时，推断当前主题与哪一个上下文相关。如果不明确，请向用户询问。
