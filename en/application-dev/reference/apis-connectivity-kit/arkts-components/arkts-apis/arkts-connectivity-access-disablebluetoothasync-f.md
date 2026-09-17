# disableBluetoothAsync

## Modules to Import

```TypeScript
import { access } from '@kit.ConnectivityKit';
```

## disableBluetoothAsync

```TypeScript
function disableBluetoothAsync(): Promise<void>
```

Asynchronous interface for disables Bluetooth on a device.

**Since:** 20

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Returns the promise object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 2900001 | Service stopped. |
| 2900013 | The user does not respond. |
| 2900014 | User refuse the action. |
| 2900099 | Operation failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    access.disableBluetoothAsync().then(() => {
        console.info('disableBluetoothAsync');
    }, (error: BusinessError) => {
        console.error('disableBluetoothAsync: errCode:' + error.code + ',errMessage' + error.message);
    })
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
