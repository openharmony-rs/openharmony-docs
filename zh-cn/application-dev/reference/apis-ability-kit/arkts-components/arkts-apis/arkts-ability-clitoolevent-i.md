# CliToolEvent

```TypeScript
export interface CliToolEvent
```

CliToolEvent用于描述CLI工具进程运行期间产生的会话事件信息。

**起始版本：** 26.0.1

<!--Device-unnamed-export interface CliToolEvent--><!--Device-unnamed-export interface CliToolEvent-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## data

```TypeScript
data: string
```

CLI工具事件数据。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CliToolEvent-data: string--><!--Device-CliToolEvent-data: string-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## toolEventType

```TypeScript
toolEventType: ToolEventType
```

CLI工具事件类型。

**类型：** [ToolEventType](arkts-ability-clitoolevent-tooleventtype-e.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CliToolEvent-toolEventType: ToolEventType--><!--Device-CliToolEvent-toolEventType: ToolEventType-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core
