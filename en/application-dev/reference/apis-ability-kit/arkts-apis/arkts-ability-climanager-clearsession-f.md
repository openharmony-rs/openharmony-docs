# clearSession

## Modules to Import

```TypeScript
import { cliManager, CliHook, ExecToolParam, ExecCmdParam, ExecResultWrap } from '@kit.AbilityKit';
```

## clearSession

```TypeScript
function clearSession(sessionId: string): Promise<void>
```

Closes a session and forcibly terminates the associated command process.

Call this method to clean up a session when the command process is no longer needed, especially for sessions running in the background. After the session is closed, the session ID becomes invalid and can no longer be used in any subsequent calls.

**Since:** 26.0.1

**Required permissions:** 
- API version 26: ohos.permission.EXEC_CLI_TOOL
- API version 26 and later: ohos.permission.EXEC_CLI_TOOL or ohos.permission.EXEC_PUBLIC_CLI_TOOL

**Model restriction:** This API can be used only in the stage model.

<!--Device-cliManager-function clearSession(sessionId: string): Promise<void>--><!--Device-cliManager-function clearSession(sessionId: string): Promise<void>-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sessionId | string | Yes | The session id of target command process. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application.<br>**Applicable version:** 26.0.0 |
| [35600032](../errorcode-ability.md#35600032-the-specified-session-does-not-exist) | The specified session does not exist. |
| [35600050](../errorcode-ability.md#35600050-occasional-error) | System Error. 1. Failed to connect to the system service; 2. The system service failed to communicate with the dependent module. |
