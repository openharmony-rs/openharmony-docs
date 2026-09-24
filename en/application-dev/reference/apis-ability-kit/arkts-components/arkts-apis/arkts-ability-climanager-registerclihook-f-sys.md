# registerCliHook (System API)

## Modules to Import

```TypeScript
import { cliManager, CliHook, ExecToolParam, ExecCmdParam, ExecResultWrap } from '@kit.AbilityKit';
```

## registerCliHook

```TypeScript
function registerCliHook(hook: CliHook): Promise<void>
```

Register a CLI hook for intercepting tool and command execution. Only one CLI hook can be registered at a time; registering again while one is already active will fail. This API is only available in developer mode. To update a registered hook, call unregisterCliHook first, then register again. The hook object must implement at least one of the optional methods in CliHook.

**Since:** 26.0.1

**Required permissions:** ohos.permission.REGISTER_AGENT_HOOK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hook | [CliHook](arkts-ability-clihook-i-sys.md) | Yes | The hook object implementing the CliHook interface. The hook object must implement at least one of the optional methods. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied, interface caller does not have permission"ohos.permission.REGISTER_AGENT_HOOK". |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. Interface caller is not a system app. |
| 35600034 | The device is not in developer mode. |
| 35600035 | A hook is already registered; unregister it first. |
| [35600050](../errorcode-ability.md#35600050-occasional-error) | System Error. 1. Connect to system service failed; 2.System service failed to communicate with dependency module. |
