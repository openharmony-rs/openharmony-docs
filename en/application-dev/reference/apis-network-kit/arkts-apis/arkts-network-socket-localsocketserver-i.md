# LocalSocketServer

```TypeScript
export interface LocalSocketServer
```

Defines a local socket server connection. Before calling LocalSocketServer APIs, you need to call [socket.constructLocalSocketServerInstance](arkts-network-socket-constructlocalsocketserverinstance-f.md) to create a **LocalSocketServer** object.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## close

```TypeScript
close(): Promise<void>
```

Stops listening for events of the **LocalSocketServer** object and releases the port bound by [listen](#listen). This API uses a promise to return the result.

> **NOTE:** 
> 
> This API does not close existing connections. To close the connection, call the [close] (#close11-1) API of
> [LocalSocketConnection] (#localsocketconnection11).

**Since:** 20

**System capability:** SystemCapability.Communication.NetStack

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [2300002](../errorcode-net-socket.md#2300002-system-internal-error) | System internal error. |

**Examples**

> NOTE
> 
> In the sample code provided in this topic, this.context is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```TypeScript
import { socket } from '@kit.NetworkKit';
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let localserver: socket.LocalSocketServer = socket.constructLocalSocketServerInstance();
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let sandboxPath: string = context.filesDir + '/testSocket';
let addr: socket.LocalAddress = {
  address: sandboxPath
}
localserver.on('connect', (connection: socket.LocalSocketConnection) => {
  console.info("connection clientId: " + connection.clientId);
  // Logical processing
  localserver.close(); // Stop event listening.
  connection.close(); // Close the current connection.
});
localserver.listen(addr).then(() => {
  console.info('listen success');
}).catch((err: BusinessError) => {
  console.error('listen fail: ' + err.code);
});
```

## getExtraOptions

```TypeScript
getExtraOptions(): Promise<ExtraOptionsBase>
```

Obtains the socket properties of the **LocalSocketServer** object. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API can be called only after **listen** is successfully called.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ExtraOptionsBase](arkts-network-socket-extraoptionsbase-i.md)&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |

**Examples**

> NOTE
> 
> In the sample code provided in this topic, this.context is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```TypeScript
import { socket } from '@kit.NetworkKit';
import { common } from '@kit.AbilityKit';

let server: socket.LocalSocketServer = socket.constructLocalSocketServerInstance();
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let sandboxPath: string = context.filesDir + '/testSocket';
let listenAddr: socket.LocalAddress = {
  address: sandboxPath
}
server.listen(listenAddr).then(() => {
  console.info("listen success");
}).catch((err: Object) => {
  console.error("listen fail: " + JSON.stringify(err));
})
server.getExtraOptions().then((options: socket.ExtraOptionsBase) => {
  console.info('options: ' + JSON.stringify(options));
}).catch((err: Object) => {
  console.error('getExtraOptions fail: ' + JSON.stringify(err));
});
```

## getLocalAddress

```TypeScript
getLocalAddress(): Promise<string>
```

Obtains the local socket address of a **LocalSocketServer** connection. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API can be called only after **listen** is successfully called.

**Since:** 12

**System capability:** SystemCapability.Communication.NetStack

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [2300002](../errorcode-net-socket.md#2300002-system-internal-error) | System internal error. |
| [2301009](../errorcode-net-socket.md#2301009-bad-file-descriptor) | Bad file descriptor. |
| [2303188](../errorcode-net-socket.md#2303188-socket-operations-on-non-sockets) | Socket operation on non-socket. |

**Examples**

> NOTE
> 
> In the sample code provided in this topic, this.context is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```TypeScript
import { common } from '@kit.AbilityKit';
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let server: socket.LocalSocketServer = socket.constructLocalSocketServerInstance();
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let sandboxPath: string = context.filesDir + '/testSocket';
let listenAddr: socket.LocalAddress = {
  address: sandboxPath
}
server.listen(listenAddr).then(() => {
  console.info("listen success");
  server.getLocalAddress().then((localPath: string) => {
    console.info("SUCCESS " + JSON.stringify(localPath));
  }).catch((err: BusinessError) => {
    console.error("FAIL " + JSON.stringify(err));
  })
}).catch((err: Object) => {
  console.error("listen fail: " + JSON.stringify(err));
})
```

## getSocketFd

```TypeScript
getSocketFd(): Promise<number>
```

Obtains the file descriptor bound to the LocalSocketServer listening port. This API uses a promise to return the result.

> **NOTE:** 
> 
> - This method can be called only after the [listen](#listen) method is successfully called.
> 
> - This API returns **-1** in abnormal cases such as listening exceptions or socket closed (for example, after close is called).
> 
> - The lifecycle of the file descriptor is managed by the system. The application can use the [close](arkts-network-socket-tcpsocketserver-i.md#close) method to close the socket connection, instead of directly operating the file descriptor.

**Since:** 23

**System capability:** SystemCapability.Communication.NetStack

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the socket file descriptor. |

**Examples**

> NOTE
> 
> In the sample code provided in this topic, this.context is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```TypeScript
import { socket } from '@kit.NetworkKit';
import { common } from '@kit.AbilityKit';

let server: socket.LocalSocketServer = socket.constructLocalSocketServerInstance();
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let sandboxPath: string = context.filesDir + '/testSocket';
let listenAddr : socket.LocalAddress = {
  address: sandboxPath
}

server.listen(listenAddr).then(() => {
  console.info("listen success");
  server.getSocketFd().then((fd: number) => {
    console.info(`Socket FD: ${fd}`);
  }).catch((err: Object) => {
    console.error(`getSocketFd fail: ${JSON.stringify(err)}`);
  });
}).catch((err: Object) => {
  console.error("listen fail: " + JSON.stringify(err));
})
```

## getState

```TypeScript
getState(): Promise<SocketStateBase>
```

Obtains the status of a local socket server connection. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API can be called only after **listen** is successfully called.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[SocketStateBase](arkts-network-socket-socketstatebase-i.md)&gt; | Promise used to return the result. |

**Examples**

> NOTE
> 
> In the sample code provided in this topic, this.context is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```TypeScript
import { socket } from '@kit.NetworkKit';
import { common } from '@kit.AbilityKit';


let server: socket.LocalSocketServer = socket.constructLocalSocketServerInstance();
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let sandboxPath: string = context.filesDir + '/testSocket';
let listenAddr: socket.LocalAddress = {
  address: sandboxPath
}
server.listen(listenAddr).then(() => {
  console.info("listen success");
}).catch((err: Object) => {
  console.error("listen fail: " + JSON.stringify(err));
})
server.getState().then((data: socket.SocketStateBase) => {
  console.info('getState success: ' + JSON.stringify(data));
}).catch((err: Object) => {
  console.error('getState fail: ' + JSON.stringify(err));
});
```

## listen

```TypeScript
listen(address: LocalAddress): Promise<void>
```

Binds the address of the local socket file. The server listens to and accepts local socket connections established over the socket. Multiple threads are used to process client data concurrently. This API uses a promise to return the result.

> **NOTE:** 
> 
> The server uses this API to complete the **bind**, **listen**, and **accept** operations. If the address of the
> local socket file is passed for binding, a socket file is automatically created when this API is called.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| address | [LocalAddress](arkts-network-socket-localaddress-i.md) | Yes | Destination address. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. If the operation is successful, no value is returned. If the operation fails, an error message is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2303109](../errorcode-net-socket.md#2303109-error-file-number) | Bad file number. |
| [2301013](../errorcode-net-socket.md#2301013-insufficient-permissions) | Insufficient permissions. |
| 2301022 | Invalid argument. |
| 2301098 | Address already in use. |

**Examples**

> NOTE
> 
> In the sample code provided in this topic, this.context is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```TypeScript
import { socket } from '@kit.NetworkKit';
import { common } from '@kit.AbilityKit';

let server: socket.LocalSocketServer = socket.constructLocalSocketServerInstance();
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let sandboxPath: string = context.filesDir + '/testSocket';
let addr: socket.LocalAddress = {
  address: sandboxPath
}
server.listen(addr).then(() => {
  console.info('listen success');
}).catch((err: Object) => {
  console.error('listen fail: ' + JSON.stringify(err));
});
```

## off('connect')

```TypeScript
off(type: 'connect', callback?: Callback<LocalSocketConnection>): void
```

Unsubscribes from **connect** events of the **LocalSocketServer** object. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'connect' | Yes | Event type.<br> 'connect': connection event. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[LocalSocketConnection](arkts-network-socket-localsocketconnection-i.md)&gt; | No | Callback used to return the result. You can pass the callback of the **on** function if you want to cancel listening for a certain type of events. If you do not pass the callback, you will cancel listening for all events. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |

**Examples**

```TypeScript
import { socket } from '@kit.NetworkKit';

let server: socket.LocalSocketServer = socket.constructLocalSocketServerInstance();
let callback = (connection: socket.LocalSocketConnection) => {
  if (connection) {
    console.info('accept a client')
  }
}
server.on('connect', callback);
// You can pass the callback of the on function if you want to cancel listening for a certain type of events. If you do not pass the callback, you will cancel listening for all events.
server.off('connect', callback);
server.off('connect');
```

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

Unsubscribes from **error** events of the **LocalSocketServer** object. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type.<br> **error**: error event. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | No | Callback used to return the result. You can pass the callback of the **on** function if you want to cancel listening for a certain type of events. If you do not pass the callback, you will cancel listening for all events. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |

**Examples**

```TypeScript
import { socket } from '@kit.NetworkKit';

let server: socket.LocalSocketServer = socket.constructLocalSocketServerInstance();
let callback = (err: Object) => {
  console.error("on error, err:" + JSON.stringify(err));
}
server.on('error', callback);
// You can pass the callback of the on function if you want to cancel listening for a certain type of events. If you do not pass the callback, you will cancel listening for all events.
server.off('error', callback);
server.off('error');
```

## on('connect')

```TypeScript
on(type: 'connect', callback: Callback<LocalSocketConnection>): void
```

Subscribes to **connect** events of the **LocalSocketServer** object. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API can be called only after **listen** is successfully called.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'connect' | Yes | Event type.<br> **connect**: connection event. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[LocalSocketConnection](arkts-network-socket-localsocketconnection-i.md)&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |

**Examples**

```TypeScript
import { socket } from '@kit.NetworkKit';

let server: socket.LocalSocketServer = socket.constructLocalSocketServerInstance();
server.on('connect', (connection: socket.LocalSocketConnection) => {
  if (connection) {
    console.info('accept a client')
  }
});
```

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

Subscribes to **error** events of the **LocalSocketServer** object. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API can be called only after **listen** is successfully called.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type.<br> **error**: error event. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |

**Examples**

```TypeScript
import { socket } from '@kit.NetworkKit';

let server: socket.LocalSocketServer = socket.constructLocalSocketServerInstance();
server.on('error', (err: Object) => {
  console.error("on error, err:" + JSON.stringify(err))
});
```

## setExtraOptions

```TypeScript
setExtraOptions(options: ExtraOptionsBase): Promise<void>
```

Sets the socket properties of the **LocalSocketServer** object. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API can be called only after **listen** is successfully called.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ExtraOptionsBase](arkts-network-socket-extraoptionsbase-i.md) | Yes | Other properties of the **LocalSocketServer** object. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2301009](../errorcode-net-socket.md#2301009-bad-file-descriptor) | Bad file descriptor. |

**Examples**

> NOTE
> 
> In the sample code provided in this topic, this.context is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```TypeScript
import { socket } from '@kit.NetworkKit';
import { common } from '@kit.AbilityKit';

let server: socket.LocalSocketServer = socket.constructLocalSocketServerInstance();
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let sandboxPath: string = context.filesDir + '/testSocket';
let listenAddr: socket.NetAddress = {
  address: sandboxPath
}
server.listen(listenAddr).then(() => {
  console.info("listen success");
}).catch((err: Object) => {
  console.error("listen fail: " + JSON.stringify(err));
})

let options: socket.ExtraOptionsBase = {
  receiveBufferSize: 8192,
  sendBufferSize: 8192,
  socketTimeout: 3000
}
server.setExtraOptions(options).then(() => {
  console.info('setExtraOptions success');
}).catch((err: Object) => {
  console.error('setExtraOptions fail: ' + JSON.stringify(err));
});
```
