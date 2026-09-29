# execCmd

## Modules to Import

```TypeScript
import { cliManager, CliHook, ExecToolParam, ExecCmdParam, ExecResultWrap } from '@kit.AbilityKit';
```

## execCmd

```TypeScript
function execCmd(cmd: string, execCmdOptions?: ExecCmdOptions): Promise<CliSessionInfo>
```

Executes a raw command string in the system shell environment.

This method accepts a free-form command string. The caller can specify a working directory, environment variables, a security policy, and an event callback through [ExecCmdOptions](arkts-ability-climanager-execcmdoptions-i.md).

If an event callback is provided in the options, the system automatically subscribes to the session events, and the callback will receive real-time output from the command process.

**Since:** 26.0.1

**Required permissions:** 
- API version 26: ohos.permission.EXEC_CLI_TOOL
- API version 26 and later: ohos.permission.EXEC_CLI_TOOL or ohos.permission.EXEC_PUBLIC_CLI_TOOL

**Model restriction:** This API can be used only in the stage model.

<!--Device-cliManager-function execCmd(cmd: string, execCmdOptions?: ExecCmdOptions): Promise<CliSessionInfo>--><!--Device-cliManager-function execCmd(cmd: string, execCmdOptions?: ExecCmdOptions): Promise<CliSessionInfo>-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cmd | string | Yes | The command to execute. |
| execCmdOptions | [ExecCmdOptions](arkts-ability-climanager-execcmdoptions-i.md) | No | The options of this action. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[CliSessionInfo](arkts-ability-climanager-clisessioninfo-i.md)&gt; | Promise used to return CliSessionInfo. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application.<br>**Applicable version:** 26.0.0 |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities.<br>**Applicable version:** 26.0.1 and later |
| [35600031](../errorcode-ability.md#35600031-maximum-number-of-concurrent-tools-reached) | Maximum number of processes has been reached. |
| [35600050](../errorcode-ability.md#35600050-occasional-error) | System Error. 1. Failed to connect to the system service; 2. The system service failed to communicate with the dependent module. |
