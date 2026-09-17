# ExecResult (System API)

Execute result of a tool execution.

**Since:** 26.0.0

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cliManager } from '@kit.AbilityKit';
```

## errorText

```TypeScript
errorText?: string
```

Indicates the error output of the tool.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## executionTime

```TypeScript
executionTime: number
```

Indicates the execution duration in milliseconds.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## exitCode

```TypeScript
exitCode?: number
```

Indicates the exit code, 0 means success.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## outputText

```TypeScript
outputText?: string
```

Indicates the standard output of the tool.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## signalNumber

```TypeScript
signalNumber?: number
```

Indicates the termination signal (if the tool process was terminated by a signal).

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## timeOut

```TypeScript
timeOut: boolean
```

Indicates whether it timed out. true means timeout occurred, false means no timeout.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.
