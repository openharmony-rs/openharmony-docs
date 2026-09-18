# createConnection

## Modules to Import

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
```

## createConnection

```TypeScript
function createConnection(deviceId: string, name: string): Connection
```

Creates a **Connection** object on the device that functions as the client. After the **Connection** object is created, subscribe to **on('connectResult')** and call **connect()** to initiate a connection request to the server. After the connection is successful, call **sendData()** to send data. If the connection is not required, call **close()** to destroy the **Connection** object to release resources.

**Since:** 20

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | Device ID of the peer device, that is, the BLE MAC address of the peer device. For details about how to obtain the BLE MAC address, see [BLE Scanning and Advertising](../../../connectivity/bluetooth/ble-development-guide.md). |
| name | string | Yes | Server name of the device to be connected. The value is a string of up to 255 bytes. It cannot be empty. If the length exceeds the upper limit or an empty string is passed, error code 32390206 is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| [Connection](arkts-distributedservice-linkenhance-connection-i.md) | **Connection** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because the linkEnhance function has been trimmed.<br>**Applicable version:** 26.0.0 and later |
| [32390206](../errorcode-link-enhance.md#32390206-invalid-parameter) | Invalid parameter. |

**Examples**

```TypeScript
On the device that functions as the client, call the createConnection() to create a Connection object.
```
