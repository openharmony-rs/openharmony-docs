# refreshActivity (System API)

## Modules to Import

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## refreshActivity

```TypeScript
function refreshActivity(reason: string): void
```

Refreshes the device activity status (for example, resetting the screen-off time).

This API takes effect only when the device is active. For details about the device activity status, see [power.isActive](arkts-basicservices-power-isactive-f.md).

**Since:** 20

**Required permissions:** ohos.permission.REFRESH_USER_ACTION

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| reason | string | Yes | Reason for refreshing the device activity status. The value must be a string. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [4900101](../errorcode-power.md#4900101-service-connection-failure) | Failed to connect to the service. |
| [4900201](../errorcode-power.md#4900201-frequent-status-refreshes) | The device activity is being refreshed too frequently; the minimum time interval is 100 ms. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. This API cannot work in car devices.<br>**Applicable version:** 26.1.0 and later |

**Examples**

```TypeScript
try {
    power.refreshActivity('refreshActivity_test');
} catch(err) {
    console.error('refreshActivity failed, err: ' + err);
}
```
