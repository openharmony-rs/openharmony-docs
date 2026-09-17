# shutdown (System API)

## Modules to Import

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## shutdown

```TypeScript
function shutdown(reason: string): void
```

Shuts down the system.

**Since:** 7

**Required permissions:** ohos.permission.REBOOT

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| reason | string | Yes | Shutdown reason. The value must be a string. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; |
| [4900101](../errorcode-power.md#4900101-service-connection-failure) | Failed to connect to the service. |

**Examples**

```TypeScript
try {
    power.shutdown('shutdown_test');
} catch(err) {
    console.error('shutdown failed, err: ' + err);
}
```
