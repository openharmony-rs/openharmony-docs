# suspend (System API)

## Modules to Import

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## suspend

```TypeScript
function suspend(isImmediate?: boolean): void
```

Enables a device to enter the sleep state.

**Since:** 9

**Required permissions:** 
- API version 19 and later: ohos.permission.POWER_MANAGER
- API versions 9 to 18: N/A

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isImmediate | boolean | No | Whether the device enters the sleep state immediately. The value **true** indicates that the device enters the sleep state immediately after the screen is turned off; **false** indicates that the system controls when the device enters the sleep state. If this parameter is not set, the default value **false** is used. If you only want to turn off the screen, you are advised not to set this parameter.<br>**NOTE:**  This parameter is supported since API version 10.<br>**Since:** 10 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Parameter verification failed. |
| [4900101](../errorcode-power.md#4900101-service-connection-failure) | Failed to connect to the service. |
| 4900701 | Failed to suspend the device. Possible causes: 1. Not allowed to turn off the screen during the exam.<br>**Applicable version:** 26.2.0 and later |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 19 and later |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. This API cannot work in car devices.<br>**Applicable version:** 26.0.1 and later |

**Examples**

```TypeScript
try {
    power.suspend();
} catch(err) {
    console.error('suspend failed, err: ' + err);
}
```
