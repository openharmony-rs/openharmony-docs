# OnEventFn

```TypeScript
type OnEventFn = (event: CliToolEvent) => void
```

定义CLI事件回调函数。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [CliToolEvent](arkts-ability-clitoolevent-i.md) | 是 | CLI工具发送的事件。 |
