# sendMessage

## Modules to Import

```TypeScript
import { cliManager, CliHook, ExecToolParam, ExecCmdParam, ExecResultWrap } from '@kit.AbilityKit';
```

## sendMessage

```TypeScript
function sendMessage(sessionId: string, message: string): Promise<void>
```

Sends a message to the standard input of a running command process.

This method allows the caller to interact with a command process that is waiting for input. The message is written to the process's standard input stream.

**Since:** 26.0.1

**Required permissions:** 
- API version 26: ohos.permission.EXEC_CLI_TOOL
- API version 26 and later: ohos.permission.EXEC_CLI_TOOL or ohos.permission.EXEC_PUBLIC_CLI_TOOL

**Model restriction:** This API can be used only in the stage model.

<!--Device-cliManager-function sendMessage(sessionId: string, message: string): Promise<void>--><!--Device-cliManager-function sendMessage(sessionId: string, message: string): Promise<void>-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sessionId | string | Yes | The session id of target command process. |
| message | string | Yes | The message to write, max length is 10240. |

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
| [35600033](../errorcode-ability.md#35600033-failed-to-write-message-to-tool-process) | Failed to write message to the tool process. |
| [35600050](../errorcode-ability.md#35600050-occasional-error) | System Error. 1. Failed to connect to the system service; 2. The system service failed to communicate with the dependent module. |
