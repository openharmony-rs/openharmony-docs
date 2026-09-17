# ExecCmdOptions (System API)

Options for executing a command.

**Since:** 26.0.0

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cliManager } from '@kit.AbilityKit';
```

## background

```TypeScript
background?: boolean
```

Indicates whether the command is executed in the background.

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## callback

```TypeScript
callback?: ToolEventCallback
```

Indicates the event callback for receiving tool events. If provided, auto-subscribe is performed.

**Type:** [ToolEventCallback](arkts-ability-tooleventcallback-i-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## challenge

```TypeScript
challenge?: string
```

Indicates the unique identifier obtained from the access token manager.

**Type:** string

**Default:** ""

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## env

```TypeScript
env?: Record<string, string>
```

Indicates the environment variables for the command.

**Type:** Record&lt;string, string&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## isShellCommand

```TypeScript
isShellCommand?: boolean
```

Indicates whether the command is executed as a shell command.

**Type:** boolean

**Default:** true

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## policy

```TypeScript
policy?: string
```

Indicates the security policy.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## timeout

```TypeScript
timeout?: number
```

Indicates the maximum execution time of the command, in seconds.

**Type:** number

**Default:** 1800

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## workDir

```TypeScript
workDir?: string
```

Indicates the working directory for the command.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## yieldMs

```TypeScript
yieldMs?: number
```

Indicates the foreground waiting timeout in milliseconds.

**Type:** number

**Default:** 0

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.
