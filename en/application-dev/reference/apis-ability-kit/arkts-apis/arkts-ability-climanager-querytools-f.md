# queryTools

## Modules to Import

```TypeScript
import { cliManager, CliHook, ExecToolParam, ExecCmdParam, ExecResultWrap } from '@kit.AbilityKit';
```

## queryTools

```TypeScript
function queryTools(): Promise<Array<ToolInfo>>
```

Query all detailed information of tools

**Since:** 26.0.1

**Required permissions:** 
- API version 26: ohos.permission.QUERY_CLI_TOOL
- API version 26 and later: ohos.permission.QUERY_CLI_TOOL or ohos.permission.QUERY_PUBLIC_CLI_TOOL

**Model restriction:** This API can be used only in the stage model.

<!--Device-cliManager-function queryTools(): Promise<Array<ToolInfo>>--><!--Device-cliManager-function queryTools(): Promise<Array<ToolInfo>>-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[ToolInfo](arkts-ability-toolinfo-i-sys.md)&gt;&gt; | List of full tool detail info. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 26.0.0 |
| [35600050](../errorcode-ability.md#35600050-occasional-error) | System Error. 1. Connect to system service failed; 2.System service failed to communicate with dependency module. |
