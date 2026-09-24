# CliSessionInfo

```TypeScript
interface CliSessionInfo
```

执行CLI工具时，系统会为调用方和CLI工具建立一个会话，此字段描述会话信息的格式。

**起始版本：** 26.0.1

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## 导入模块

```TypeScript
import { cliManager, CliHook, ExecToolParam, ExecCmdParam, ExecResultWrap } from '@kit.AbilityKit';
```

## result

```TypeScript
result?: ExecResult
```

工具执行结果。默认值：undefined。

**类型：** [ExecResult](arkts-ability-climanager-execresult-i.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## sessionId

```TypeScript
sessionId: string
```

会话id。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## status

```TypeScript
status: SessionStatus
```

会话状态。

**类型：** [SessionStatus](arkts-ability-climanager-sessionstatus-e.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## toolName

```TypeScript
toolName: string
```

工具名称。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core
