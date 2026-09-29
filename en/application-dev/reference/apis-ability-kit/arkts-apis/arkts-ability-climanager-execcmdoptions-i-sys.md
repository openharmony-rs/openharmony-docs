# ExecCmdOptions

```TypeScript
interface ExecCmdOptions
```

Describes the options for executing a raw command string via [execCmd](arkts-ability-climanager-execcmd-f.md).

**Since:** 26.0.1

<!--Device-cliManager-interface ExecCmdOptions--><!--Device-cliManager-interface ExecCmdOptions-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## Modules to Import

```TypeScript
import { cliManager, CliHook, ExecToolParam, ExecCmdParam, ExecResultWrap } from '@kit.AbilityKit';
```

## challenge

```TypeScript
challenge?: string
```

Indicates the unique identifier obtained from the access token manager.

**Type:** string

**Default:** ""

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExecCmdOptions-challenge?: string--><!--Device-ExecCmdOptions-challenge?: string-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## dmSessionId

```TypeScript
dmSessionId?: string
```

Indicates the session ID of the dialog manager (DM), which uniquely identifies the agent session. The value consists of letters, digits, '_' and '-', with a maximum length of 256.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExecCmdOptions-dmSessionId?: string--><!--Device-ExecCmdOptions-dmSessionId?: string-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## isShellCommand

```TypeScript
isShellCommand?: boolean
```

Indicates whether the command is executed as a shell command.

**Type:** boolean

**Default:** true

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExecCmdOptions-isShellCommand?: boolean--><!--Device-ExecCmdOptions-isShellCommand?: boolean-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## toolCallId

```TypeScript
toolCallId?: string
```

Indicates the unique identifier assigned to a tool call by the agent. The value consists of letters, digits, '_' and '-', with a maximum length of 256.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExecCmdOptions-toolCallId?: string--><!--Device-ExecCmdOptions-toolCallId?: string-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.
