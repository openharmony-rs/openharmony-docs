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

## background

```TypeScript
background?: boolean
```

Indicates whether the command is executed in the background.

When set to **true**, the [execCmd](arkts-ability-climanager-execcmd-f.md) method returns immediately after the command process is created. When set to **false**, the method blocks until the command finishes or the foreground waiting timeout (yieldMs) expires.

**Type:** boolean

**Default:** false

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExecCmdOptions-background?: boolean--><!--Device-ExecCmdOptions-background?: boolean-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## callback

```TypeScript
callback?: ToolEventCallback
```

Indicates the event callback for receiving tool events.

If provided, the system automatically subscribes to the session events (such as stdout, stderr, exit, and error) of the tool process. The callback receives CliToolEvent objects as events arrive. This is equivalent to calling [subscribeSession](arkts-ability-climanager-subscribesession-f.md) manually after execution.

**Type:** [ToolEventCallback](arkts-ability-tooleventcallback-i.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExecCmdOptions-callback?: ToolEventCallback--><!--Device-ExecCmdOptions-callback?: ToolEventCallback-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## env

```TypeScript
env?: Record<string, string>
```

Indicates the environment variables for the command.

The keys are variable names and the values are their corresponding string values. These variables are injected into the execution environment of the command process.

**Type:** Record&lt;string, string&gt;

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExecCmdOptions-env?: Record<string, string>--><!--Device-ExecCmdOptions-env?: Record<string, string>-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## policy

```TypeScript
policy?: string
```

Indicates the security policy.

The policy string is interpreted by the system service to enforce additional security constraints on the command. The format and available policies are defined by the system security module.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExecCmdOptions-policy?: string--><!--Device-ExecCmdOptions-policy?: string-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## timeout

```TypeScript
timeout?: number
```

Indicates the maximum execution time of the command, in seconds.

If the command process runs longer than this duration, it is forcibly terminated and the [timeOut](arkts-ability-climanager-execresult-i.md#timeout) field is set to **true**.

**Type:** number

**Default:** 1800

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExecCmdOptions-timeout?: long--><!--Device-ExecCmdOptions-timeout?: long-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## workDir

```TypeScript
workDir?: string
```

Indicates the working directory for the command.

If not specified, the default working directory of the system service is used.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExecCmdOptions-workDir?: string--><!--Device-ExecCmdOptions-workDir?: string-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## yieldMs

```TypeScript
yieldMs?: number
```

Indicates the foreground waiting timeout in milliseconds.

This value is effective only when background is **false**. It specifies how long the caller waits for the command to complete in the foreground. If the command does not finish within this duration, the method returns a session ID and the command continues running in the background. A value of 0 means the caller waits until the command finishes or the maximum execution timeout (timeout) is reached.

**Type:** number

**Default:** 0

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExecCmdOptions-yieldMs?: long--><!--Device-ExecCmdOptions-yieldMs?: long-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core
