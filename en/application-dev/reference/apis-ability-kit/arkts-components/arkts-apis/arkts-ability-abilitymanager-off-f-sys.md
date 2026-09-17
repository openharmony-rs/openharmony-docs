# off (System API)

## Modules to Import

```TypeScript
import { abilityManager } from '@kit.AbilityKit';
```

## off('abilityForegroundState')

```TypeScript
function off(type: 'abilityForegroundState', observer?: AbilityForegroundStateObserver): void
```

Unregisters the observer used to listen for ability start or exit events.

**Since:** 11

**Required permissions:** ohos.permission.RUNNING_STATE_OBSERVER

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'abilityForegroundState' | Yes | Event type. It is fixed at **'abilityForegroundState'**. |
| observer | [AbilityForegroundStateObserver](arkts-ability-abilitymanager-abilityforegroundstateobserver-t-sys.md) | No | Observer used to listen for ability start or exit events. If this parameter is not set, all observers associated with the specified event are deregistered. If this parameter is set, only the specified observer is deregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. Interface caller is not a system app. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
