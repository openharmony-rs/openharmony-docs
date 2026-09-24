# pairDeviceOutOfBand (System API)

## Modules to Import

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## pairDeviceOutOfBand

```TypeScript
function pairDeviceOutOfBand(transport: BluetoothTransport, p192Data: OobData | null,
    p256Data: OobData | null): Promise<void>
```

Starts pairing with a remote Bluetooth device using the Out Of Band mechanism. This function is asynchronous, and the pairing status is obtained by listening to the bondStateChange event. If both p192Data and p256Data are null, the function call will fail. If both p192Data and p256Data are used simultaneously, p256Data takes effect.

**Since:** 23

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| transport | [BluetoothTransport](arkts-connectivity-connection-bluetoothtransport-e.md) | Yes | Indicates the transport of a remote Bluetooth device. |
| p192Data | [OobData](arkts-connectivity-connection-oobdata-i-sys.md) &#124; null | Yes | The out-of-band data (P192), or null if not available. |
| p256Data | [OobData](arkts-connectivity-connection-oobdata-i-sys.md) &#124; null | Yes | The out-of-band data (P256), or null if not available. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Returns the promise object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications are not allowed to use system APIs. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 2900003 | Bluetooth disabled. |
| 2900099 | Operation failed. |

**Examples**

```TypeScript
import { common } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let transport: connection.BluetoothTransport = connection.BluetoothTransport.TRANSPORT_LE;
    let addressInfo: common.BluetoothAddress = {
        "address": "11:22:33:44:55:66",
        "addressType": common.BluetoothAddressType.REAL, // The value must be an actual MAC address.
        "rawAddressType": common.BluetoothRawAddressType.RANDOM
    };
    let confirmHash: Uint8Array = new Uint8Array([0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x0A, 0x0B, 0x0C, 0x0D, 0x0E, 0x0F, 0x10]);
    let randomHash: Uint8Array = new Uint8Array([0x11, 0x22, 0x33, 0x44, 0x55, 0x66, 0x77, 0x88, 0x99, 0xAA, 0xBB, 0xCC, 0xDD, 0xEE, 0xFF, 0x11]);
    let oobData: connection.OobData = {
        "deviceId": addressInfo,
        "confirmationHash": confirmHash,
        "randomizerHash": randomHash,
        "deviceName": "testName",
        "deviceRole": connection.DeviceRole.DEVICE_ROLE_PERIPHERAL_ONLY
    }
    connection.pairDeviceOutOfBand(transport, null, oobData).then(() => {
        console.info('pairDeviceOufOfBand');
    }, (err: BusinessError) => {
        console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
    });
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```
