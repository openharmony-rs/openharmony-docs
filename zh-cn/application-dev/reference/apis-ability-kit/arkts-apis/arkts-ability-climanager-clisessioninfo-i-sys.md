# CliSessionInfo（系统接口）

执行CLI工具时，系统会为调用方和CLI工具建立一个会话，此字段描述会话信息的格式。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cliManager } from '@kit.AbilityKit';
```

## result

```TypeScript
result?: ExecResult
```

工具执行结果。默认值：undefined。

**类型：** [ExecResult](arkts-ability-climanager-execresult-i-sys.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## sessionId

```TypeScript
sessionId: string
```

会话id。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## status

```TypeScript
status: SessionStatus
```

会话状态。

**类型：** [SessionStatus](arkts-ability-climanager-sessionstatus-e-sys.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

## toolName

```TypeScript
toolName: string
```

工具名称。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。
