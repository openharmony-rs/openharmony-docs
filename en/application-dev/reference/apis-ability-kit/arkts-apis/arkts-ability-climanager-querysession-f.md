# querySession

## Modules to Import

```TypeScript
import { cliManager, CliHook, ExecToolParam, ExecCmdParam, ExecResultWrap } from '@kit.AbilityKit';
```

## querySession

```TypeScript
function querySession(sessionId: string): Promise<CliSessionInfo>
```

Queries the current status and execution result of a session.

Use this method to poll the status of a background session, or to retrieve the execution result after a session has completed. The returned [CliSessionInfo](arkts-ability-climanager-clisessioninfo-i.md) includes the session ID, tool name, current status, and execution result (if the session has finished).

**Since:** 26.0.1

**Required permissions:** 
- API version 26: ohos.permission.EXEC_CLI_TOOL
- API version 26 and later: ohos.permission.EXEC_CLI_TOOL or ohos.permission.EXEC_PUBLIC_CLI_TOOL

**Model restriction:** This API can be used only in the stage model.

<!--Device-cliManager-function querySession(sessionId: string): Promise<CliSessionInfo>--><!--Device-cliManager-function querySession(sessionId: string): Promise<CliSessionInfo>-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sessionId | string | Yes | The session id of target command process. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[CliSessionInfo](arkts-ability-climanager-clisessioninfo-i.md)&gt; | The info of target session. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application.<br>**Applicable version:** 26.0.0 |
| [35600032](../errorcode-ability.md#35600032-the-specified-session-does-not-exist) | The specified session does not exist. |
| [35600050](../errorcode-ability.md#35600050-occasional-error) | System Error. 1. Failed to connect to the system service; 2. The system service failed to communicate with the dependent module. |
