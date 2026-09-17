# wakeup (System API)

## Modules to Import

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## wakeup

```TypeScript
function wakeup(detail: string): void
```

Wakes up a device.

**Since:** 9

**Required permissions:** 
- API version 19 and later: ohos.permission.POWER_MANAGER
- API versions 9 to 18: N/A

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| detail | string | Yes | Wakeup reason. The value must be a string. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; |
| [4900101](../errorcode-power.md#4900101-service-connection-failure) | Failed to connect to the service. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 19 and later |

**Examples**

```TypeScript
try {
    power.wakeup('wakeup_test');
} catch(err) {
    console.error('wakeup failed, err: ' + err);
}
```
