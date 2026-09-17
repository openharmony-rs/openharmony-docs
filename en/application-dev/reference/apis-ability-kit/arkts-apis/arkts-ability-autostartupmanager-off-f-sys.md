# off (System API)

## Modules to Import

```TypeScript
import { autoStartupManager } from '@kit.AbilityKit';
```

## off('systemAutoStartup')

```TypeScript
function off(type: 'systemAutoStartup', callback?: AutoStartupCallback): void
```

Unregisters the callback used to listen for auto-startup status changes of an application component. Starting from API version 18, this API can be properly called on 2-in-1 devices and wearables. If it is called on other device types, error code 16000050 is returned. For versions earlier than API version 18, this API can be properly called only on 2-in-1 devices. If it is called on other device types, error code 16000050 is returned.

**Since:** 11

**Required permissions:** ohos.permission.MANAGE_APP_BOOT

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'systemAutoStartup' | Yes | Event type. The value is fixed at **systemAutoStartup**, which can be called only by system applications. |
| callback | [AutoStartupCallback](arkts-ability-autostartupcallback-i-sys.md) | No | Callback used for unregistration. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied, interface caller does not have permission"ohos.permission.MANAGE_APP_BOOT". |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Failed to connect to the system service. |
