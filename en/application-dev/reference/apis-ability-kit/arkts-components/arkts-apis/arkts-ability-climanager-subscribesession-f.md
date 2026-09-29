# subscribeSession

## Modules to Import

```TypeScript
import { cliManager, CliHook, ExecToolParam, ExecCmdParam, ExecResultWrap } from '@kit.AbilityKit';
```

## subscribeSession

```TypeScript
function subscribeSession(sessionId: string, callback: ToolEventCallback): Promise<void>
```

Subscribes to events from a CLI tool or command execution session.

After subscribing, the provided callback will receive CliToolEvent objects whenever the command process produces output (stdout/stderr), exits, or encounters an error. This is useful for real-time monitoring of long-running command processes.

If an event callback was already provided in [ExecCmdOptions](arkts-ability-climanager-execcmdoptions-i.md) when calling [execCmd](arkts-ability-climanager-execcmd-f.md), manual subscription is not necessary.

**Since:** 26.0.1

**Required permissions:** 
- API version 26: ohos.permission.EXEC_CLI_TOOL
- API version 26 and later: ohos.permission.EXEC_CLI_TOOL or ohos.permission.EXEC_PUBLIC_CLI_TOOL

**Model restriction:** This API can be used only in the stage model.

<!--Device-cliManager-function subscribeSession(sessionId: string, callback: ToolEventCallback): Promise<void>--><!--Device-cliManager-function subscribeSession(sessionId: string, callback: ToolEventCallback): Promise<void>-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sessionId | string | Yes | The session id of target command process. |
| callback | [ToolEventCallback](arkts-ability-tooleventcallback-i.md) | Yes | The callback to receive session events. |

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
