# CliSessionInfo (System API)

Session information of a tool execution.

**Since:** 26.0.0

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cliManager } from '@kit.AbilityKit';
```

## result

```TypeScript
result?: ExecResult
```

Indicates the execution result, has a value when status is completed or failed.

**Type:** [ExecResult](arkts-ability-climanager-execresult-i-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## sessionId

```TypeScript
sessionId: string
```

Indicates id of this session.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## status

```TypeScript
status: SessionStatus
```

Indicates status of session.

**Type:** [SessionStatus](arkts-ability-climanager-sessionstatus-e-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## toolName

```TypeScript
toolName: string
```

Indicates name of tool.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.
