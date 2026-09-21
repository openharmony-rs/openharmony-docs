# Connection

```TypeScript
interface Connection
```

Represents a **Connection** object, which provides methods for connecting to and disconnecting from a peer device, obtaining the device's ID, sending data, and registering or unregistering event callbacks.

**Since:** 20

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## Modules to Import

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
```

## close

```TypeScript
close(): void
```

Destroys the **Connection** object to release resources. If the device needs to interact with the peer device again, create a **Connection** object again and call **connect()** to initiate a connection. **close()** is called to destroy the **Connection** object and release resources. If the call is successful, the **Connection** object needs to be re-created when it is needed again. **disconnect()** is called for disconnection. If the call is successful, the **Connection** object can still be connected. If the connection needs to be re-established, call **disconnect()**. If the service is no longer needed, call **close()**.

**Since:** 20

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |

**Examples**

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "testDemo";

try {
  let peerDeviceId: string = "00:11:22:33:44:55";
  hilog.info(0x0000, TAG, 'connection server deviceId = ' + peerDeviceId);
  let connection: linkEnhance.Connection = linkEnhance.createConnection(peerDeviceId, "demo");
  connection.on('connectResult', (result: linkEnhance.ConnectResult): void => {
    hilog.info(0x0000, TAG, 'clientConnectResultCallback result = ' + result.success);
    if (result.success) {
      connection.close();
    }
  });
  connection.connect();
} catch (err) {
  hilog.error(0x0000, TAG, 'errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}
```

## connect

```TypeScript
connect(): void
```

Connects to the server on the client after the **Connection** object is successfully created. A maximum number of 10 connections are supported. You are advised to register a callback listener using **on('connectResult')** and then call this method to obtain the connection result. After the connection is successful, you can call **sendData()** to send data. When the connection is no longer needed, call **disconnect()** to disconnect from the server.

**Since:** 20

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [32390204](../errorcode-link-enhance.md#32390204-number-of-connections-exceeding-the-limit) | The number of connection exceeds the limit. |
| [32390300](../errorcode-link-enhance.md#32390300-internal-error) | Internal error. |

**Examples**

After creating a Connection object, the application on the client device calls connect() to connect to the target device (that is, the server).

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "testDemo";

try {
  let peerDeviceId: string = "00:11:22:33:44:55";
  hilog.info(0x0000, TAG, 'connection server deviceId = ' + peerDeviceId);
  let connection: linkEnhance.Connection = linkEnhance.createConnection(peerDeviceId, "demo");
  // Subscribe to connectResult events.
  connection.on('connectResult', (result: linkEnhance.ConnectResult): void => {
    hilog.info(0x0000, TAG, 'clientConnectResultCallback result = ' + result.success);
  });
  // Initiate a connection.
  connection.connect();
} catch (err) {
  hilog.error(0x0000, TAG, 'errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}
```

## disconnect

```TypeScript
disconnect(): void
```

Disconnects from the peer device. The created **Connection** object remains valid after this API is called. You can call **connect()** to reconnect to the peer device if necessary.

**Since:** 20

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |

**Examples**

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "testDemo";

try {
  let peerDeviceId: string = "00:11:22:33:44:55";
  hilog.info(0x0000, TAG, 'connection server deviceId = ' + peerDeviceId);
  let connection: linkEnhance.Connection = linkEnhance.createConnection(peerDeviceId, "demo");
  connection.on('connectResult', (result: linkEnhance.ConnectResult): void => {
    hilog.info(0x0000, TAG, 'clientConnectResultCallback result = ' + result.success);
    if (result.success) {
      connection.disconnect();
    }
  });
  connection.connect();
} catch (err) {
  hilog.error(0x0000, TAG, 'errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}
```

## getPeerDeviceId

```TypeScript
getPeerDeviceId(): string
```

Obtains the device ID of the peer device. This API is called when the connection is established successfully either by initiating a connection or accepting an incoming connection.

**Since:** 20

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Return value:**

| Type | Description |
| --- | --- |
| string | Device ID of the peer device, that is, the BLE MAC address of the peer device. An empty string is returned if no device ID is obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |

**Examples**

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "testDemo";

try {
  let peerDeviceId: string = "00:11:22:33:44:55";
  hilog.info(0x0000, TAG, 'connection server deviceId = ' + peerDeviceId);
  let connection: linkEnhance.Connection = linkEnhance.createConnection(peerDeviceId, "demo");
  hilog.info(0x0000, TAG, "peerDeviceId=%{public}s", connection.getPeerDeviceId());
} catch (err) {
  hilog.error(0x0000, TAG, 'errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}
```

## off('connectResult')

```TypeScript
off(type: 'connectResult', callback?: Callback<ConnectResult>): void
```

Unregisters the listener for **connectResult** events.

**Since:** 20

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'connectResult' | Yes | Event type, which is **connectResult**. This event is triggered when `connect()` is called. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ConnectResult](arkts-distributedservice-linkenhance-connectresult-i.md)&gt; | No | Registered callback. The callback last registered using **on** needs to be passed to unregister the callback. The default effect is the same as the passing behavior. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [32390206](../errorcode-link-enhance.md#32390206-invalid-parameter) | Invalid parameter. |

**Examples**

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "testDemo";

try {
  let peerDeviceId: string = "00:11:22:33:44:55";
  hilog.info(0x0000, TAG, 'connection server deviceId = ' + peerDeviceId);
  let connection: linkEnhance.Connection = linkEnhance.createConnection(peerDeviceId, "demo");
  connection.on('connectResult', (result: linkEnhance.ConnectResult): void => {
    hilog.info(0x0000, TAG, 'clientConnectResultCallback result = ' + result.success);
  });
  // Unsubscribe from connectResult events.
  connection.off('connectResult', (result: linkEnhance.ConnectResult): void => {
    hilog.info(0x0000, TAG, 'clientConnectResultCallback result = ' + result.success);
  });
} catch (err) {
  hilog.error(0x0000, TAG, 'errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}
```

## off('disconnected')

```TypeScript
off(type: 'disconnected', callback?: Callback<number>): void
```

Unregisters the listener for **disconnected** events. This API uses an asynchronous callback to return the result.

**Since:** 20

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'disconnected' | Yes | Event type, which is **disconnected**. This event is triggered when the connection is passively terminated or an exception occurs. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | No | Registered callback, where **number** indicates the returned error code. This event is triggered when the connection is passively terminated or an exception occurs. The callback last registered using **on** needs to be passed to unregister the callback. The default effect is the same as the passing behavior. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [32390206](../errorcode-link-enhance.md#32390206-invalid-parameter) | Invalid parameter. |

**Examples**

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "testDemo";

try {
  let peerDeviceId: string = "00:11:22:33:44:55";
  hilog.info(0x0000, TAG, 'connection server deviceId = ' + peerDeviceId);
  let connection: linkEnhance.Connection = linkEnhance.createConnection(peerDeviceId, "demo");
  connection.on('disconnected', (number: number) => {
    hilog.info(0x0000, TAG, 'connection disconnected reason = ' + number);
  });
  // Unsubscribe from disconnected events.
  connection.off('disconnected', (number: number) => {
    hilog.info(0x0000, TAG, 'connection disconnected reason = ' + number);
  });
} catch (err) {
  hilog.error(0x0000, TAG, 'errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}
```

## off('dataReceived')

```TypeScript
off(type: 'dataReceived', callback?: Callback<ArrayBuffer>): void
```

Unregisters the listener for **dataReceived** events.

**Since:** 20

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'dataReceived' | Yes | Event type, which is **dataReceived**. This event is triggered when data is received. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;ArrayBuffer&gt; | No | Callback used to receive data from the peer device. The callback parameter **data** is the received data, which is of the ArrayBuffer type. The callback last registered using **on** needs to be passed to unregister the callback. The default effect is the same as the passing behavior. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [32390206](../errorcode-link-enhance.md#32390206-invalid-parameter) | Invalid parameter. |

**Examples**

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "testDemo";

try {
  let peerDeviceId: string = "00:11:22:33:44:55";
  hilog.info(0x0000, TAG, 'connection server deviceId = ' + peerDeviceId);
  let connection: linkEnhance.Connection = linkEnhance.createConnection(peerDeviceId, "demo");
  // Subscribe to data receiving notifications.
  connection.on('dataReceived', (data: ArrayBuffer) => {
    hilog.info(0x0000, TAG, 'recv dataLen = ' + data.byteLength);
  });
  // Unsubscribe from data receiving notifications.
  connection.off('dataReceived', (data: ArrayBuffer) => {
    hilog.info(0x0000, TAG, 'recv dataLen = ' + data.byteLength);
  });
} catch (err) {
  hilog.error(0x0000, TAG, 'errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}
```

## on('connectResult')

```TypeScript
on(type: 'connectResult', callback: Callback<ConnectResult>): void
```

Registers a listener for **connectResult** events. This API uses an asynchronous callback to return the result. You must register this listener before calling **connect()**. Otherwise, the connection result cannot be obtained. When the listener is no longer needed, you are advised to call **off('connectResult')** to unregister the listener to prevent memory leak.

**Since:** 20

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'connectResult' | Yes | Event type, which is **connectResult**. This event is triggered when `connect()` is called. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ConnectResult](arkts-distributedservice-linkenhance-connectresult-i.md)&gt; | Yes | Registered callback. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [32390206](../errorcode-link-enhance.md#32390206-invalid-parameter) | Invalid parameter. |

**Examples**

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "testDemo";

try {
  let peerDeviceId: string = "00:11:22:33:44:55";
  hilog.info(0x0000, TAG, 'connection server deviceId = ' + peerDeviceId);
  let connection: linkEnhance.Connection = linkEnhance.createConnection(peerDeviceId, "demo");
  // Subscribe to connectResult events.
  connection.on('connectResult', (result: linkEnhance.ConnectResult): void => {
    hilog.info(0x0000, TAG, 'clientConnectResultCallback result = ' + result.success);
  });

  // Initiate a connection.
  connection.connect();
} catch (err) {
  hilog.error(0x0000, TAG, 'errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}
```

## on('disconnected')

```TypeScript
on(type: 'disconnected', callback: Callback<number>): void
```

Registers a listener for **disconnected** events. This API uses an asynchronous callback to return the result.

**Since:** 20

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'disconnected' | Yes | Event type, which is **disconnected**. This event is triggered when the connection is passively terminated or an exception occurs. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | Yes | Registered callback, where **number** indicates the returned error code. This event is triggered when the connection is passively terminated or an exception occurs. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [32390206](../errorcode-link-enhance.md#32390206-invalid-parameter) | Invalid parameter. |

**Examples**

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "testDemo";

try {
  let peerDeviceId: string = "00:11:22:33:44:55";
  hilog.info(0x0000, TAG, 'connection server deviceId = ' + peerDeviceId);
  let connection: linkEnhance.Connection = linkEnhance.createConnection(peerDeviceId, "demo");
  // Subscribe to disconnected events.
  connection.on('disconnected', (number: number) => {
    hilog.info(0x0000, TAG, 'connection disconnected reason = ' + number);
  });
} catch (err) {
  hilog.error(0x0000, TAG, 'errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}
```

## on('dataReceived')

```TypeScript
on(type: 'dataReceived', callback: Callback<ArrayBuffer>): void
```

Registers a listener for the **dataReceived** events. This API uses an asynchronous callback to return the result.

**Since:** 20

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'dataReceived' | Yes | Event type, which is **dataReceived**. This event is triggered when data is received. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;ArrayBuffer&gt; | Yes | Callback used to receive data from the peer device. The callback parameter **data** is the received data, which is of the **ArrayBuffer** type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [32390206](../errorcode-link-enhance.md#32390206-invalid-parameter) | Invalid parameter. |

**Examples**

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "testDemo";

try {
  let peerDeviceId: string = "00:11:22:33:44:55";
  hilog.info(0x0000, TAG, 'connection server deviceId = ' + peerDeviceId);
  let connection: linkEnhance.Connection = linkEnhance.createConnection(peerDeviceId, "demo");
  // Initiate a connection.
  connection.connect();
  // Subscribe to data receiving notifications.
  connection.on('dataReceived', (data: ArrayBuffer) => {
    hilog.info(0x0000, TAG, 'recv dataLen = ' + data.byteLength);
  });
} catch (err) {
  hilog.error(0x0000, TAG, 'errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}
```

## sendData

```TypeScript
sendData(data: ArrayBuffer): void
```

Sends data to the server after a connection is established successfully. When the server receives the connection callback, it can also send data to the client.

**Since:** 20

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | ArrayBuffer | Yes | Data to send. The maximum length is 1024 bytes. If the length exceeds the upper limit, error code 32390206 is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [32390206](../errorcode-link-enhance.md#32390206-invalid-parameter) | Invalid parameter. |
| [32390205](../errorcode-link-enhance.md#32390205-connection-unavailable) | Connection is not ready. |
| [32390300](../errorcode-link-enhance.md#32390300-internal-error) | Internal error. |

**Examples**

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = "testDemo";

try {
  let peerDeviceId: string = "00:11:22:33:44:55";
  hilog.info(0x0000, TAG, 'connection server deviceId = ' + peerDeviceId);
  let connection: linkEnhance.Connection = linkEnhance.createConnection(peerDeviceId, "demo");
  connection.on('connectResult', (result: linkEnhance.ConnectResult): void => {
    hilog.info(0x0000, TAG, 'clientConnectResultCallback result = ' + result.success);
    if (result.success) {
      let len = 1;
      let arrayBuffer = new ArrayBuffer(len); // Create the data to send.
      connection.sendData(arrayBuffer);
      hilog.info(0x0000, TAG, "sendData data connection peerDeviceId=%{public}s", connection.getPeerDeviceId());
      connection.disconnect();
    }
  });
  connection.connect();
} catch (err) {
  hilog.error(0x0000, TAG, 'errCode: ' + (err as BusinessError).code + ', errMessage: ' +
  (err as BusinessError).message);
}
```
