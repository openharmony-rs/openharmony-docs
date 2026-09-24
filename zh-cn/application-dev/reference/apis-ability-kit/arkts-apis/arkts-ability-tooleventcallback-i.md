# ToolEventCallback

```TypeScript
export interface ToolEventCallback
```

ToolEventCallback用于接收CLI工具进程运行期间产生的会话事件。

@interface ToolEventCallback

**起始版本：** 26.0.1

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## onEvent

```TypeScript
onEvent: OnEventFn
```

CLI工具会话事件回调函数。

@typedef { OnEventFn }

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core
