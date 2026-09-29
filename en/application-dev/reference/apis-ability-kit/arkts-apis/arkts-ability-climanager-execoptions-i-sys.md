# ExecOptions (System API)

```TypeScript
interface ExecOptions
```

Tool execution options.

**Since:** 26.0.0

<!--Device-cliManager-interface ExecOptions--><!--Device-cliManager-interface ExecOptions-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cliManager, CliHook, ExecToolParam, ExecCmdParam, ExecResultWrap } from '@kit.AbilityKit';
```

## background

```TypeScript
background?: boolean
```

Indicates whether the tool is executed in the background.

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExecOptions-background?: boolean--><!--Device-ExecOptions-background?: boolean-End-->

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

<!--Device-ExecOptions-dmSessionId?: string--><!--Device-ExecOptions-dmSessionId?: string-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## timeout

```TypeScript
timeout?: number
```

Indicates the maximum execution time of the tool, in seconds. The value should be a long.

**Type:** number

**Default:** 1800

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExecOptions-timeout?: long--><!--Device-ExecOptions-timeout?: long-End-->

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

<!--Device-ExecOptions-toolCallId?: string--><!--Device-ExecOptions-toolCallId?: string-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## yieldMs

```TypeScript
yieldMs?: number
```

Indicates the foreground waiting timeout in milliseconds. The value should be a long.

**Type:** number

**Default:** 0

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExecOptions-yieldMs?: long--><!--Device-ExecOptions-yieldMs?: long-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.
