# unregisterCliHook (System API)

## Modules to Import

```TypeScript
import { cliManager, CliHook, ExecToolParam, ExecCmdParam, ExecResultWrap } from '@kit.AbilityKit';
```

## unregisterCliHook

```TypeScript
function unregisterCliHook(hook: CliHook): Promise<void>
```

Unregister the previously registered CLI hook. The hook object must be the same as the one passed to registerCliHook. If no hook is registered, the call will fail with an error.

**Since:** 26.0.1

**Required permissions:** ohos.permission.REGISTER_AGENT_HOOK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hook | [CliHook](arkts-ability-clihook-i-sys.md) | Yes | The hook object to unregister. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied, interface caller does not have permission"ohos.permission.REGISTER_AGENT_HOOK". |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. Interface caller is not a system app. |
| 35600036 | No hook is registered; nothing to unregister. |
| [35600050](../errorcode-ability.md#35600050-occasional-error) | System Error. 1. Connect to system service failed; 2.System service failed to communicate with dependency module. |
