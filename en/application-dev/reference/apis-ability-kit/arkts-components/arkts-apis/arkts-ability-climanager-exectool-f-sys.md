# execTool (System API)

## Modules to Import

```TypeScript
import { cliManager } from '@kit.AbilityKit';
```

## execTool

```TypeScript
function execTool(toolName: string, subCommand: string, args: Record<string, Object>, challenge: string,
    execOptions?: ExecOptions): Promise<CliSessionInfo>
```

Execute a CLI command

**Since:** 26.0.0

**Required permissions:** ohos.permission.EXEC_CLI_TOOL

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| toolName | string | Yes | The name of target tool. |
| subCommand | string | Yes | The subCommand of this execute action. |
| args | Record&lt;string, Object&gt; | Yes | The input args of tool. |
| challenge | string | Yes | The unique identifier get from access token manager. |
| execOptions | [ExecOptions](arkts-ability-climanager-execoptions-i-sys.md) | No | The options of this action. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[CliSessionInfo](arkts-ability-climanager-clisessioninfo-i-sys.md)&gt; | execute result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied, interface caller does not have permission"ohos.permission.EXEC_CLI_TOOL". |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. Interface caller is not a system app. |
| [35600030](../errorcode-ability.md#35600030-cli-tool-does-not-exist) | No tool with the specified name exists. |
| [35600031](../errorcode-ability.md#35600031-maximum-number-of-concurrent-tools-reached) | Maximum number of processes has been reached. |
| [35600050](../errorcode-ability.md#35600050-occasional-error) | System Error. 1. Connect to system service failed; 2. The system service failed to communicate with the dependent module. |
