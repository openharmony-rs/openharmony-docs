# isValidRandomDeviceId

## Modules to Import

```TypeScript
import { access } from '@kit.ConnectivityKit';
```

## isValidRandomDeviceId

```TypeScript
function isValidRandomDeviceId(deviceId: string): boolean
```

Determine whether the randomized device address application can still be used.

**Since:** 16

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Atomic service API:** This API can be used in atomic services since API version 16.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | the randomized address of remote device. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns whether the randomized device address is valid. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 2900003 | Bluetooth disabled. |
| 2900099 | Check persistent device address failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let deviceId = '11:22:33:44:55:66' // The address can be obtained through BLE scanning.
    let isValid = access.isValidRandomDeviceId(deviceId);
    console.info("isValid: " + isValid);
} catch (err) {
    console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
}
```
