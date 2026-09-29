# CliSessionInfo

```TypeScript
interface CliSessionInfo
```

Describes the session information of a CLI tool or command execution.

**Since:** 26.0.1

<!--Device-cliManager-interface CliSessionInfo--><!--Device-cliManager-interface CliSessionInfo-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## Modules to Import

```TypeScript
import { cliManager, CliHook, ExecToolParam, ExecCmdParam, ExecResultWrap } from '@kit.AbilityKit';
```

## result

```TypeScript
result?: ExecResult
```

Indicates the execution result, has a value when status is completed or failed.

**Type:** [ExecResult](arkts-ability-climanager-execresult-i.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-CliSessionInfo-result?: ExecResult--><!--Device-CliSessionInfo-result?: ExecResult-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## sessionId

```TypeScript
sessionId: string
```

Indicates the unique identifier of this session.

This ID is used in subsequent calls to [subscribeSession](arkts-ability-climanager-subscribesession-f.md), [querySession](arkts-ability-climanager-querysession-f.md), [sendMessage](arkts-ability-climanager-sendmessage-f.md), and [clearSession](arkts-ability-climanager-clearsession-f.md) to manage the session lifecycle.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-CliSessionInfo-sessionId: string--><!--Device-CliSessionInfo-sessionId: string-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## status

```TypeScript
status: SessionStatus
```

Indicates status of session.

**Type:** [SessionStatus](arkts-ability-climanager-sessionstatus-e.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-CliSessionInfo-status: SessionStatus--><!--Device-CliSessionInfo-status: SessionStatus-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## toolName

```TypeScript
toolName: string
```

Indicates the name of the tool being executed.

For [execCmd](arkts-ability-climanager-execcmd-f.md), this field is set to "shell".

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-CliSessionInfo-toolName: string--><!--Device-CliSessionInfo-toolName: string-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core
