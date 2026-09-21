# off

## Modules to Import

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## off('BLEDeviceFind')

```TypeScript
function off(type: 'BLEDeviceFind', callback?: Callback<Array<ScanResult>>): void
```

Unsubscribe BLE scan result. On API 10 and above, the permission required by this interface is changed from USE_BLUETOOTH to ACCESS_BLUETOOTH.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** BLEDeviceFind

**Required permissions:** 
- API version 10 and later: ohos.permission.ACCESS_BLUETOOTH
- API version 9: ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'BLEDeviceFind' | Yes | Type of the scan result event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[ScanResult](arkts-connectivity-ble-scanresult-i.md)&gt;&gt; | No | Callback used to listen for the scan result event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 2900099 | Operation failed. |

**Examples**

```TypeScript
import { BusinessError } from '@ohos.base';
function onReceiveEvent(data: Array<bluetoothManager.ScanResult>) {
    console.info('bluetooth device find = '+ JSON.stringify(data));
}
try {
    bluetoothManager.BLE.on('BLEDeviceFind', onReceiveEvent);
    bluetoothManager.BLE.off('BLEDeviceFind', onReceiveEvent);
} catch (err) {
    console.error("errCode:" + (err as BusinessError).code + ",errMessage:" + (err as BusinessError).message);
}
```
