# Server

Represents a **Server** object, which provides methods for starting, stopping, and closing the server, and registering or unregistering event callbacks.

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

Destroys the **Server** object to release related resources. To interact with the peer device again, create a new **Server** object. **close()** is called to destroy the **Server** object and release resources. If the call is successful, the **Server** object needs to be re-created when it is needed again. **stop()** is called to stop the server. If the call is successful, the **Server** object can still be restarted. If the server needs to be restarted, use **stop()**. If the server is no longer needed, use **close()**.

**Since:** 20

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |

## off('connectionAccepted')

```TypeScript
off(type: 'connectionAccepted', callback?: Callback<Connection>): void
```

Unregisters the callback listener for **connectionAccepted** event. This API must be called after the server is successfully created. This API uses an asynchronous callback to return the result.

**Since:** 20

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'connectionAccepted' | Yes | Event type, which is **connectionAccepted**. This event is triggered when a connection from the peer end is received. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Connection](arkts-distributedservice-linkenhance-connection-i.md)&gt; | No | Registered callback. The parameter is [Connection](arkts-distributedservice-linkenhance-connection-i.md). The callback last registered using **on** needs to be passed to unregister the callback. The default effect is the same as the passing behavior. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [32390206](../errorcode-link-enhance.md#32390206-invalid-parameter) | Invalid parameter. |

## off('serverStopped')

```TypeScript
off(type: 'serverStopped', callback?: Callback<number>): void
```

Unregisters the callback listener for **serverStopped** event. This API must be called after the server is created successfully. This API uses an asynchronous callback to return the result.

**Since:** 20

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'serverStopped' | Yes | Event type, which is **serverStopped**. This event is triggered when the server is stopped abnormally. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | No | Registered callback, where **number** indicates the returned error code. This event is triggered when the server is stopped abnormally. The callback last registered using **on** needs to be passed to unregister the callback. The default effect is the same as the passing behavior. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [32390206](../errorcode-link-enhance.md#32390206-invalid-parameter) | Invalid parameter. |

## on('connectionAccepted')

```TypeScript
on(type: 'connectionAccepted', callback: Callback<Connection>): void
```

Registers a callback listener for **connectionAccepted** events. This API uses an asynchronous callback to return the result.

**Since:** 20

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'connectionAccepted' | Yes | Event type, which is **connectionAccepted**. This event is triggered when a connection from the peer end is received. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Connection](arkts-distributedservice-linkenhance-connection-i.md)&gt; | Yes | Callback used to receive server connection events. The callback parameter **connection** is the connection object used to establish the connection. The type is [Connection](arkts-distributedservice-linkenhance-connection-i.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [32390206](../errorcode-link-enhance.md#32390206-invalid-parameter) | Invalid parameter. |

## on('serverStopped')

```TypeScript
on(type: 'serverStopped', callback: Callback<number>): void
```

Registers a callback listener for **serverStopped** events. This API uses an asynchronous callback to return the result.

**Since:** 20

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'serverStopped' | Yes | Event type, which is **serverStopped**. This event is triggered when the server is stopped abnormally. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | Yes | Registered callback, where **number** indicates the returned error code. This event is triggered when the server is stopped abnormally. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [32390206](../errorcode-link-enhance.md#32390206-invalid-parameter) | Invalid parameter. |

## start

```TypeScript
start(): void
```

Starts a server so that it can be connected by the client. A maximum of 10 servers are supported. After a server is started, you can stop it by calling **stop()** and restart it by calling **start()**. After using the server, call **close()** to destroy the **Server** object to release resources.

**Since:** 20

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [32390202](../errorcode-link-enhance.md#32390202-number-of-services-exceeding-the-limit) | The number of servers exceeds the limit. |
| [32390300](../errorcode-link-enhance.md#32390300-internal-error) | Internal error. |

## stop

```TypeScript
stop(): void
```

Stops the server. After the server is stopped, you can call `start` to start it again.

**Since:** 20

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
