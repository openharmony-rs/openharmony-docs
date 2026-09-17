# getRemoteProductId (System API)

## Modules to Import

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## getRemoteProductId

```TypeScript
function getRemoteProductId(deviceId: string): string
```

Obtains the product ID of a remote device.

**Since:** 11

**Required permissions:** 
- API version 16 and later: N/A
- API versions 11 to 15: ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | Indicates device ID. For example, "11:22:33:AA:BB:FF". |

**Return value:**

| Type | Description |
| --- | --- |
| string | Returns the remote device's product ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied.<br>**Applicable version:** 11 - 15 |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications are not allowed to use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 2900001 | Service stopped. |
| 2900003 | Bluetooth disabled. |
| 2900099 | Operation failed. |

**Examples**

```TypeScript
try {
  let remoteDeviceProductId = connection.getRemoteProductId('XX:XX:XX:XX:XX:XX');
} catch (err) {
  console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
}
```
