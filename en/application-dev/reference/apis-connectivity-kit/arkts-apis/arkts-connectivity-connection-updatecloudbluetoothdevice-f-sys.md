# updateCloudBluetoothDevice (System API)

## Modules to Import

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## updateCloudBluetoothDevice

```TypeScript
function updateCloudBluetoothDevice(trustedPairedDevices: TrustedPairedDevices): Promise<void>
```

update cloud devices.

**Since:** 15

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| trustedPairedDevices | [TrustedPairedDevices](arkts-connectivity-connection-trustedpaireddevices-i-sys.md) | Yes | Indicates the cloud devices. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Returns the promise object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications are not allowed to use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 2900001 | Service stopped. |
| 2900003 | Bluetooth disabled. |
| 2900099 | Operation failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// promise
/**
 * Update cloud devices in Bluetooth settings.
 */
const trustPairDeviceArr: connection.TrustedPairedDevice[] = [];
let descBuffer = new ArrayBuffer(1);
trustPairDeviceArr.push({
    sn: '',
    deviceType: '',
    modelId: '',
    manufactory: '',
    productId: '',
    hiLinkVersion: '',
    macAddress: '11:22:33:44:55:66',
    serviceType: '',
    serviceId: '',
    deviceName: '',
    uuids: '',
    bluetoothClass: 0,
    token: descBuffer,
    deviceNameTime: 0,
    secureAdvertisingInfo: descBuffer,
    pairState: 0
    });
const trustPairDevices: connection.TrustedPairedDevices = { trustedPairedDevices: trustPairDeviceArr };
try {
    connection.updateCloudBluetoothDevice(trustPairDevices)
        .then(() => {
            console.info('updateCloudBluetoothDevice success!');
        })
        .catch((err: BusinessError) => {
            console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
        });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
