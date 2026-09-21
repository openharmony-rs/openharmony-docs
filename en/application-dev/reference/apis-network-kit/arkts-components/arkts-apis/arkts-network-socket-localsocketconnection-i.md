# LocalSocketConnection

```TypeScript
export interface LocalSocketConnection
```

Defines a local socket connection, that is, the session between the local socket client and the server. Before calling LocalSocketConnection APIs, you need to obtain a **LocalSocketConnection** object.

> **NOTE:** 
> 
> The LocalSocketConnection client can call related APIs through the **LocalSocketConnection** object only after a
> connection is successfully established between the local socket client and the server.

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

Closes a local socket connection. This API uses a promise to return the result.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [2301009](../errorcode-net-socket.md#2301009-bad-file-descriptor) | Bad file descriptor. |

**Examples**

```TypeScript
import { socket } from '@kit.NetworkKit';

let server: socket.LocalSocketServer = socket.constructLocalSocketServerInstance();
server.on('connect', (connection: socket.LocalSocketConnection) => {
  connection.close().then(() => {
    console.info('close success');
  }).catch((err: Object) => {
    console.error('close fail: ' + JSON.stringify(err));
  });
});
```

## getLocalAddress

```TypeScript
getLocalAddress(): Promise<string>
```

Obtains the local socket address of a **LocalSocketConnection** connection. This API uses a promise to return the result.

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
let localAddr: socket.LocalAddress = {
  address: sandboxPath
}
server.listen(localAddr).then(() => {
  console.info('listen success');
  let client: socket.LocalSocket = socket.constructLocalSocketInstance();
  let connectOpt: socket.LocalConnectOptions = {
    address: localAddr,
    timeout: 6000
  }
  client.connect(connectOpt).then(() => {
    server.getLocalAddress().then((localPath: string) => {
      console.info("success, localPath is" + JSON.stringify(localPath));
    }).catch((err: BusinessError) => {
      console.error("FAIL " + JSON.stringify(err));
    })
  }).catch((err: Object) => {
    console.error('connect fail: ' + JSON.stringify(err));
  });
});
```

## getSocketFd

```TypeScript
getSocketFd(): Promise<number>
```

Obtains the file descriptor of a LocalSocketConnection connection. This API uses a promise to return the result.

> **NOTE:** 
> 
> - This method can be called only after a connection is set up.
> 
> - This API returns **-1** in abnormal cases such as disconnection and socket closed (for example, after the close API is called).
> 
> - The lifecycle of the file descriptor is managed by the system. The application can use the [close](arkts-network-socket-localsocket-i.md#close) method to close the socket connection, instead of directly operating the file descriptor.

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
server.on('connect', (connection: socket.LocalSocketConnection) => {
  connection.getSocketFd().then((fd: number) => {
    console.info(`Socket FD: ${fd}`);
  }).catch((err: Object) => {
    console.error(`getSocketFd fail: ${JSON.stringify(err)}`);
  });
});
server.listen(listenAddr).then(() => {
  console.info("listen success");
}).catch((err: Object) => {
  console.error(`listen fail: ${JSON.stringify(err)}`);
})
```

## off('message')

```TypeScript
off(type: 'message', callback?: Callback<LocalSocketMessageInfo>): void
```

Unsubscribes from **message** events of the **LocalSocketConnection** object. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'message' | Yes | Event type.<br> **message**: message receiving event. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[LocalSocketMessageInfo](arkts-network-socket-localsocketmessageinfo-i.md)&gt; | No | Callback used to return the result. You can pass the callback of the **on** function if you want to cancel listening for a certain type of events. If you do not pass the callback, you will cancel listening for all events. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |

**Examples**

```TypeScript
import { socket } from '@kit.NetworkKit';

let server: socket.LocalSocketServer = socket.constructLocalSocketServerInstance();
let callback = (value: socket.LocalSocketMessageInfo) => {
  const uintArray = new Uint8Array(value.message)
  let messageView = '';
  for (let i = 0; i < uintArray.length; i++) {
    messageView += String.fromCharCode(uintArray[i]);
  }
  console.info('total: ' + JSON.stringify(value));
  console.info('message information: ' + messageView);
}
server.on('connect', (connection: socket.LocalSocketConnection) => {
  connection.on('message', callback);
  // You can pass the callback of the on function if you want to cancel listening for a certain type of events. If you do not pass the callback, you will cancel listening for all events.
  connection.off('message', callback);
  connection.off('message');
});
```

## off('close')

```TypeScript
off(type: 'close', callback?: Callback<void>): void
```

Unsubscribes from **close** events of the **LocalSocketConnection** object. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'close' | Yes | Event type.<br> **close**: close event. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | No | Callback used to return the result. You can pass the callback of the **on** function if you want to cancel listening for a certain type of events. If you do not pass the callback, you will cancel listening for all events. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |

**Examples**

```TypeScript
import { socket } from '@kit.NetworkKit';

let server: socket.LocalSocketServer = socket.constructLocalSocketServerInstance();
let callback = () => {
  console.info("on close success");
}
server.on('connect', (connection: socket.LocalSocketConnection) => {
  connection.on('close', callback);
  // You can pass the callback of the on function if you want to cancel listening for a certain type of events. If you do not pass the callback, you will cancel listening for all events.
  connection.off('close', callback);
  connection.off('close');
});
```

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

Unsubscribes from **error** events of the **LocalSocketConnection** object. This API uses an asynchronous callback to return the result.

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

let callback = (err: Object) => {
  console.error("on error, err: " + JSON.stringify(err));
}
let server: socket.LocalSocketServer = socket.constructLocalSocketServerInstance();
server.on('connect', (connection: socket.LocalSocketConnection) => {
  connection.on('error', callback);
  // You can pass the callback of the on function if you want to cancel listening for a certain type of events. If you do not pass the callback, you will cancel listening for all events.
  connection.off('error', callback);
  connection.off('error');
});
```

## on('message')

```TypeScript
on(type: 'message', callback: Callback<LocalSocketMessageInfo>): void
```

Subscribes to **message** events of the **LocalSocketConnection** object. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'message' | Yes | Event type.<br> **message**: message receiving event. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[LocalSocketMessageInfo](arkts-network-socket-localsocketmessageinfo-i.md)&gt; | Yes | Callback used to return the result. |

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
});
server.on('connect', (connection: socket.LocalSocketConnection) => {
  connection.on('message', (value: socket.LocalSocketMessageInfo) => {
    const uintArray = new Uint8Array(value.message);
    let messageView = '';
    for (let i = 0; i < uintArray.length; i++) {
      messageView += String.fromCharCode(uintArray[i]);
    }
    console.info('total: ' + JSON.stringify(value));
    console.info('message information: ' + messageView);
  });
});
```

## on('close')

```TypeScript
on(type: 'close', callback: Callback<void>): void
```

Unsubscribes from **close** events of the **LocalSocketConnection** object. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'close' | Yes | Event type.<br> **close**: close event. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |

**Examples**

```TypeScript
import { socket } from '@kit.NetworkKit';

let server: socket.LocalSocketServer = socket.constructLocalSocketServerInstance();
server.on('connect', (connection: socket.LocalSocketConnection) => {
  connection.on('close', () => {
    console.info("on close success")
  });
});
```

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

Subscribes to **error** events of the **LocalSocketConnection** object. This API uses an asynchronous callback to return the result.

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
server.on('connect', (connection: socket.LocalSocketConnection) => {
  connection.on('error', (err: Object) => {
    console.error("on error, err:" + JSON.stringify(err))
  });
});
```

## send

```TypeScript
send(options: LocalSendOptions): Promise<void>
```

Sends data through a local socket connection. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API can be used only after the server obtains a **LocalSocketConnection** object through the **callback**
> of the **connect** event.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [LocalSendOptions](arkts-network-socket-localsendoptions-i.md) | Yes | Parameters for sending data over a local socket connection. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| 2301011 | Operation would block. |

**Examples**

```TypeScript
import { socket } from '@kit.NetworkKit';

let server: socket.LocalSocketServer = socket.constructLocalSocketServerInstance();

server.on('connect', (connection: socket.LocalSocketConnection) => {
  let sendOptions: socket.LocalSendOptions = {
    data: 'Hello, client!'
  }
  connection.send(sendOptions).then(() => {
    console.info('send success');
  }).catch((err: Object) => {
    console.error('send fail: ' + JSON.stringify(err));
  });
});
```

## clientId

```TypeScript
clientId: number
```

ID of the session between the client and the server.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack
