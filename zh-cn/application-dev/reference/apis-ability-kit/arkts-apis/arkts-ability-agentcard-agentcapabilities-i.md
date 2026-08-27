# AgentCapabilities

定义Agent支持的可选能力。

**起始版本：** 24

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## extendedAgentCard

```TypeScript
extendedAgentCard?: boolean
```

Agent是否支持在认证时提供扩展的AgentCard。true：表示支持，客户端在通过认证后可以获取包含额外信息（如私有配置、高级能力）的扩展AgentCard。false：表示仅提供基础AgentCard。不传入时默认为false。

**类型：** boolean

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## extension

```TypeScript
extension?: string
```

Agent支持的协议扩展。用于存储自定义的扩展能力配置，格式为JSON字符串，可以包含协议级别的扩展参数和自定义字段，由开发者和Agent使用方约定。不配置时不使用扩展配置。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## pushNotifications

```TypeScript
pushNotifications?: boolean
```

Agent是否支持为异步任务更新发送推送通知。true：表示支持，当长时间运行的任务状态发生变化时（如任务完成、失败或进度更新），Agent可以主动推送通知给客户端。false：表示不支持，客户端需要轮询查询任务状态。

**类型：** boolean

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## stateTransitionHistory

```TypeScript
stateTransitionHistory?: boolean
```

Agent是否支持查看任务状态变化历史。true：表示支持，客户端可以查询任务从创建到完成的完整状态转换记录（如pending-&gt;running-&gt;completed）。false：表示不支持状态历史查询。

**类型：** boolean

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## streaming

```TypeScript
streaming?: boolean
```

Agent是否支持流式响应。true：表示支持SSE（Server-Sent Events）流式响应，实时返回部分结果。false：表示不支持流式，仅支持一次性返回完整结果。启用流式响应后，客户端可使用stream方法获取实时数据流。

**类型：** boolean

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core
