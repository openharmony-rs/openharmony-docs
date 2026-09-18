# generateLocalOobData (System API)

## Modules to Import

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## generateLocalOobData

```TypeScript
function generateLocalOobData(transport: BluetoothTransport): Promise<OobData>
```

Generate out-of-band data of the local device.

**Since:** 23

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| transport | [BluetoothTransport](arkts-connectivity-connection-bluetoothtransport-e.md) | Yes | Indicates the transport of a remote Bluetooth device. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[OobData](arkts-connectivity-connection-oobdata-i-sys.md)&gt; | Returns the out-of-band data. |

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
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let transport: connection.BluetoothTransport = connection.BluetoothTransport.TRANSPORT_LE;
    connection.generateLocalOobData(transport).then((oobData: connection.OobData) => {
        console.info(`generateLocalOobData: ${JSON.stringify(oobData)}`);
    }, (err: BusinessError) => {
        console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
    });
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```
