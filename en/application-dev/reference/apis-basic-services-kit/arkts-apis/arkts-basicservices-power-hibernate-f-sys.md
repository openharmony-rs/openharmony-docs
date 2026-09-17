# hibernate (System API)

## Modules to Import

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## hibernate

```TypeScript
function hibernate(clearMemory: boolean): void
```

Hibernates a device.

**Since:** 12

**Required permissions:** 
- API version 19 and later: ohos.permission.POWER_MANAGER
- API versions 12 to 18: N/A

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| clearMemory | boolean | Yes | Whether to clear the memory. The value **true** means to clear the memory before the system enters the hibernation state, and the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Parameter verification failed. |
| [4900101](../errorcode-power.md#4900101-service-connection-failure) | Failed to connect to the service. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 19 and later |

**Examples**

```TypeScript
try {
    power.hibernate(true);
} catch(err) {
    console.error('hibernate failed, err: ' + err);
}
```
