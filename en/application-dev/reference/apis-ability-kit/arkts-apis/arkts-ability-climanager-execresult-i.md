# ExecResult

```TypeScript
interface ExecResult
```

Describes the execution result of a tool or command.

**Since:** 26.0.1

<!--Device-cliManager-interface ExecResult--><!--Device-cliManager-interface ExecResult-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## Modules to Import

```TypeScript
import { cliManager, CliHook, ExecToolParam, ExecCmdParam, ExecResultWrap } from '@kit.AbilityKit';
```

## errorText

```TypeScript
errorText?: string
```

Indicates the error output (stderr) content of the tool.

This field captures all text written by the tool to its standard error stream during execution. Note that some tools write diagnostic information to stderr even when execution succeeds.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExecResult-errorText?: string--><!--Device-ExecResult-errorText?: string-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## executionTime

```TypeScript
executionTime: number
```

Indicates the execution duration in milliseconds. The value range is all integers.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExecResult-executionTime: long--><!--Device-ExecResult-executionTime: long-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## exitCode

```TypeScript
exitCode?: number
```

Indicates the exit code, 0 means success. The value range is all integers.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExecResult-exitCode?: int--><!--Device-ExecResult-exitCode?: int-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## outputText

```TypeScript
outputText?: string
```

Indicates the standard output (stdout) content of the tool.

This field captures all text written by the tool or command to its standard output stream during execution.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExecResult-outputText?: string--><!--Device-ExecResult-outputText?: string-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## signalNumber

```TypeScript
signalNumber?: number
```

Indicates the termination signal (if the tool process was terminated by a signal). The value range is all integers.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExecResult-signalNumber?: int--><!--Device-ExecResult-signalNumber?: int-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## timeOut

```TypeScript
timeOut: boolean
```

Indicates whether it timed out.

When **true**, the tool process was forcibly terminated because it exceeded the maximum execution timeout. When **false**, the tool finished within the allowed time.

**Type:** boolean

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExecResult-timeOut: boolean--><!--Device-ExecResult-timeOut: boolean-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core
