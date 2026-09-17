# execCmd (System API)

## Modules to Import

```TypeScript
import { cliManager } from '@kit.AbilityKit';
```

## execCmd

```TypeScript
function execCmd(cmd: string, execCmdOptions?: ExecCmdOptions): Promise<CliSessionInfo>
```

Execute a command. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.EXEC_CLI_TOOL

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cmd | string | Yes | The command to execute. |
| execCmdOptions | [ExecCmdOptions](arkts-ability-climanager-execcmdoptions-i-sys.md) | No | The options of this action. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[CliSessionInfo](arkts-ability-climanager-clisessioninfo-i-sys.md)&gt; | Promise used to return CliSessionInfo. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [35600031](../errorcode-ability.md#35600031-maximum-number-of-concurrent-tools-reached) | Maximum number of processes has been reached. |
| [35600050](../errorcode-ability.md#35600050-occasional-error) | System Error. 1. Failed to connect to the system service; 2. The system service failed to communicate with the dependent module. |
