# WebSocketServer

```TypeScript
export interface WebSocketServer
```

Defines a **WebSocketServer** object. You need to use [webSocket.createWebSocketServer](arkts-network-websocket-createwebsocketserver-f.md) to create a **WebSocketServer** object before using its methods.

**Since:** 19

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { webSocket } from '@kit.NetworkKit';
```

## close

```TypeScript
close(connection: WebSocketConnection, options?: webSocket.WebSocketCloseOptions): Promise<boolean>
```

Closes a WebSocket connection. This API uses a promise to return the result.

**Since:** 19

**Required permissions:** ohos.permission.INTERNET

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| connection | [WebSocketConnection](arkts-network-websocket-websocketconnection-i.md) | Yes | Client information, including the IP address and port number. |
| options | [webSocket.WebSocketCloseOptions](arkts-network-websocket-websocketcloseoptions-i.md) | No | Optional parameters carried in the request for closing a WebSocket connection.<br>By default, the error code is 200, and the cause is **Websocket connect failed**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the operation is successful, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| 2302006 | websocket connection does not exist. |

**Examples**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let localServer: webSocket.WebSocketServer;
let config: webSocket.WebSocketServerConfig = {
  serverPort: 8080, // Listening port
  maxConcurrentClientsNumber: 10,
  maxConnectionsForOneClient: 10,
}

localServer = webSocket.createWebSocketServer();
localServer.start(config).then((success: boolean) => {
  if (success) {
    console.info('webSocket server start success');
  } else {
    console.error('websocket server start failed');
  }
}).catch((error: BusinessError) => {
  console.error(`Failed to start. Code: ${error.code}, message: ${error.message}`);
});

localServer.on('connect', (connection: webSocket.WebSocketConnection) => {
  console.info(`New client connected! Client ip: ${connection.clientIP}, Client port: ${connection.clientPort}`);
  localServer.close(connection).then((success: boolean) => {
    if (success) {
      console.info('close client successfully');
    } else {
      console.error('close client failed');
    }
  });
});
```

## listAllConnections

```TypeScript
listAllConnections(): WebSocketConnection[]
```

Obtains information about all clients connected to the server.

**Required permission**: ohos.permission.INTERNET

> **NOTE:** 
> 
> This API is called asynchronously. The **await** keyword needs to be used to wait until the asynchronous
> operation is complete, ensuring that information about all clients connected to the server can be correctly
> obtained.

**Since:** 19

**Required permissions:** ohos.permission.INTERNET

**System capability:** SystemCapability.Communication.NetStack

**Return value:**

| Type | Description |
| --- | --- |
| [WebSocketConnection](arkts-network-websocket-websocketconnection-i.md)[] | an array consists connections from all clients. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |

**Examples**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let connections: webSocket.WebSocketConnection[] = [];
let localServer: webSocket.WebSocketServer;
let config: webSocket.WebSocketServerConfig = {
  serverPort: 8080, // Listening port
  maxConcurrentClientsNumber: 10,
  maxConnectionsForOneClient: 10,
}

localServer = webSocket.createWebSocketServer();
localServer.start(config).then((success: boolean) => {
  if (success) {
    console.info('webSocket server start success');
  } else {
    console.error('websocket server start failed');
  }
}).catch((error: BusinessError) => {
  console.error(`Failed to start. Code: ${error.code}, message: ${error.message}`);
});

localServer.on('connect', async (connection: webSocket.WebSocketConnection) => {
  console.info(`New client connected! Client ip: ${connection.clientIP}, Client port: ${connection.clientPort}`);
  try {
    connections = await localServer.listAllConnections();
    if (connections.length === 0) {
      console.info('client list is empty');
    } else {
      console.info(`client list cnt: ${connections.length}, client connections list is: ${connections}`);
    }
  } catch (error) {
    console.error(`Failed to listAllConnections. Code: ${error.code}, message: ${error.message}`);
  }
});
```

## off('connect')

```TypeScript
off(type: 'connect', callback?: Callback<WebSocketConnection>): void
```

Unsubscribes from WebSocketServer connection events (the connection between the client and server is successfully established). This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> You can pass the callback of the **on** function if you want to cancel listening for a certain type of event.
> If you do not pass the callback, you will cancel listening for all events.

**Since:** 19

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'connect' | Yes | Event type, which has a fixed value of **connect**. Successful calling of **offconnect()** indicates that listening for connection events is canceled successful. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[WebSocketConnection](arkts-network-websocket-websocketconnection-i.md)&gt; | No | Callback used to return the information about connected clients. |

**Examples**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let localServer = webSocket.createWebSocketServer();
localServer.off('connect');
```

## off('messageReceive')

```TypeScript
off(type: 'messageReceive', callback?: Callback<WebSocketMessage>): void
```

Unsubscribes from the WebSocketServer event of receiving client messages. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> You can pass the callback of the **on** function if you want to cancel listening for a certain type of event.
> If you do not pass the callback, you will cancel listening for all events.

**Since:** 19

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'messageReceive' | Yes | Event type, which has a fixed value of **messageReceive**. Successful calling of **offmessageReceive()** indicates that listening for **messageReceive** events is canceled successfully. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[WebSocketMessage](arkts-network-websocket-websocketmessage-i.md)&gt; | No | Callback used to return the result, which contains:<br>- **clientconnection**: client information. <br>- **data**: data sent by the client. |

**Examples**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError, Callback } from '@kit.BasicServicesKit';

let localServer = webSocket.createWebSocketServer();
localServer.off('messageReceive');
```

## off('close')

```TypeScript
off(type: 'close', callback?: ClientConnectionCloseCallback): void
```

Unsubscribes from WebSocketServer close events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> You can pass the callback of the **on** function if you want to cancel listening for a certain type of event.
> If you do not pass the callback, you will cancel listening for all events.

**Since:** 19

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'close' | Yes | Event type, which has a fixed value of **close**. Successful calling of **offclose()** indicates that listening for the **close** events is canceled successfully. |
| callback | [ClientConnectionCloseCallback](arkts-network-websocket-clientconnectionclosecallback-t.md) | No | Callback used to return the result.<br>**close** and **reason** indicate the error code and error cause for closing the connection, respectively. |

**Examples**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let localServer = webSocket.createWebSocketServer();
localServer.off('close');
```

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

Unsubscribes from WebSocketServer error events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> You can pass the callback of the **on** function if you want to cancel listening for a certain type of event.
> If you do not pass the callback, you will cancel listening for all events.

**Since:** 19

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type, which has a fixed value of **error**. Successful calling of **offerror()** indicates that listening for the **error** events is canceled successfully. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | No | Callback used to return the error code (default value: **200**). |

**Examples**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let localServer = webSocket.createWebSocketServer();
localServer.off('error');
```

## on('connect')

```TypeScript
on(type: 'connect', callback: Callback<WebSocketConnection>): void
```

Subscribes to the WebSocketServer connection event (the connection between the client and server is successfully established). This API uses an asynchronous callback to return the result.

**Since:** 19

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'connect' | Yes | Event type, which has a fixed value of **connect**. Successful calling of **onconnect()** indicates that a connection is established between the client and server. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[WebSocketConnection](arkts-network-websocket-websocketconnection-i.md)&gt; | Yes | Callback used to return the information about connected clients. |

**Examples**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError, Callback } from '@kit.BasicServicesKit';

let localServer = webSocket.createWebSocketServer();
localServer.on('connect', (connection: webSocket.WebSocketConnection) => {
  console.info(`New client connected! Client ip: ${connection.clientIP}, Client port: ${connection.clientPort}`);
});
```

## on('messageReceive')

```TypeScript
on(type: 'messageReceive', callback: Callback<WebSocketMessage>): void
```

Subscribes to the WebSocketServer event of receiving client messages. This API uses an asynchronous callback to return the result.

**Since:** 19

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'messageReceive' | Yes | Event type, which has a fixed value of **messageReceive**. Successful calling of **onmessageReceive()** indicates that a message is received from the client. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[WebSocketMessage](arkts-network-websocket-websocketmessage-i.md)&gt; | Yes | Callback used to return the result.<br>**clientconnection** indicates the client information and **data** indicates the data message sent by the client. |

**Examples**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError, Callback } from '@kit.BasicServicesKit';

let localServer = webSocket.createWebSocketServer();
localServer.on('messageReceive', (message: webSocket.WebSocketMessage) => {
  console.info(`on message received, client: ${message.clientConnection}, data: ${message.data}`);
});
```

## on('close')

```TypeScript
on(type: 'close', callback: ClientConnectionCloseCallback): void
```

Subscribes to WebSocketServer close events. This API uses an asynchronous callback to return the result.

**Since:** 19

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'close' | Yes | Event type, which has a fixed value of **close**. Successful calling of **onclose()** indicates that the connection is closed successfully. |
| callback | [ClientConnectionCloseCallback](arkts-network-websocket-clientconnectionclosecallback-t.md) | Yes | Callback used to return the result.<br>**close** and **reason** indicate the error code and error cause for closing the connection, respectively. |

**Examples**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let localServer = webSocket.createWebSocketServer();
localServer.on('close', (clientConnection: webSocket.WebSocketConnection, closeReason: webSocket.CloseResult) => {
  console.info(`client close, client: ${clientConnection}, closeReason: Code: ${closeReason.code}, reason: ${closeReason.reason}`);
});
```

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

Subscribes to WebSocketServer error events. This API uses an asynchronous callback to return the result.

**Since:** 19

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type, which has a fixed value of **error**. Successful calling of **onerror()** indicates that an error has occurred. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let wsServer: webSocket.WebSocketServer = webSocket.createWebSocketServer();
wsServer.on('error', (err: BusinessError) => {
  console.error(`error. Code: ${err.code}, message: ${err.message}`);
});
```

## send

```TypeScript
send(data: string | ArrayBuffer, connection: WebSocketConnection): Promise<boolean>
```

Sends data through the WebSocket connection. This API uses a promise to return the result.

> **NOTE:** 
> 
> The **send** API can be called only after a **connect** event is listened.
> **Required permission**: ohos.permission.INTERNET

**Since:** 19

**Required permissions:** ohos.permission.INTERNET

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string &#124; ArrayBuffer | Yes | Data to send, which can be of the string or ArrayBuffer type. A maximum of 5,242,864 bytes (that is, 5 x 1024 x 1024 - 16) can be sent. If the data size exceeds the upper limit, error code 401 will be returned. |
| connection | [WebSocketConnection](arkts-network-websocket-websocketconnection-i.md) | Yes | Client information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the operation is successful, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| 2302006 | websocket connection does not exist. |

**Examples**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let localServer: webSocket.WebSocketServer;
let config: webSocket.WebSocketServerConfig = {
  serverPort: 8080, // Listening port
  maxConcurrentClientsNumber: 10,
  maxConnectionsForOneClient: 10,
}

localServer = webSocket.createWebSocketServer();
localServer.start(config).then((success: boolean) => {
  if (success) {
    console.info('webSocket server start success');
  } else {
    console.error('websocket server start failed');
  }
}).catch((error: BusinessError) => {
  console.error(`Failed to start. Code: ${error.code}, message: ${error.message}`);
});

localServer.on('connect', async (connection: webSocket.WebSocketConnection) => {
  console.info(`New client connected! Client ip: ${connection.clientIP}, Client port: ${connection.clientPort}`);
  // Use send() to send data to the client when the on('connect') event is received.
  localServer.send("Hello, I'm server!", connection).then((success: boolean) => {
    if (success) {
      console.info('message send successfully');
    } else {
      console.error('message send failed');
    }
  }).catch((error: BusinessError) => {
    console.error(`message send failed, Code: ${error.code}, message: ${error.message}`);
  });
});
```

## start

```TypeScript
start(config: WebSocketServerConfig): Promise<boolean>
```

Starts the WebSocketServer service based on the specified **config**. This API uses a promise to return the result.

> **NOTE:** 
> 
> You are advised not to listen for the same port when calling this API multiple times.
> **Required permission**: ohos.permission.INTERNET

**Since:** 19

**Required permissions:** ohos.permission.INTERNET

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [WebSocketServerConfig](arkts-network-websocket-websocketserverconfig-i.md) | Yes | Starts the WebSocket server. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the operation is successful, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [2302002](../errorcode-net-webSocket.md#2302002-websocket-certificate-does-not-exist) | Websocket certificate file does not exist. |
| [2302004](../errorcode-net-webSocket.md#2302004-listening-failed-on-the-specified-nic) | Can't listen on the given NIC. |
| [2302005](../errorcode-net-webSocket.md#2302005-listening-failed-on-the-specified-port) | Can't listen on the given Port. |
| [2302999](../errorcode-net-webSocket.md#2302999-internal-error) | Websocket other unknown error. |
| [2302007](../errorcode-net-webSocket.md#2302007-listening-port-already-occupied) | Websocket port already occupied.<br>**Applicable version:** 24 and later |

**Examples**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let localServer: webSocket.WebSocketServer;
let config: webSocket.WebSocketServerConfig = {
  serverPort: 8080, // Listening port
  maxConcurrentClientsNumber: 10,
  maxConnectionsForOneClient: 10,
}

localServer = webSocket.createWebSocketServer();
localServer.start(config).then((success: boolean) => {
  if (success) {
    console.info('webSocket server start success');
  } else {
    console.error('websocket server start failed');
  }
}).catch((error: BusinessError) => {
  console.error(`Failed to start. Code: ${error.code}, message: ${error.message}`);
});
```

## stop

```TypeScript
stop(): Promise<boolean>
```

Stops the WebSocketServer service. This API uses a promise to return the result.

**Since:** 19

**Required permissions:** ohos.permission.INTERNET

**System capability:** SystemCapability.Communication.NetStack

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the operation is successful, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |

**Examples**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let localServer: webSocket.WebSocketServer;
let config: webSocket.WebSocketServerConfig = {
  serverPort: 8080, // Listening port
  maxConcurrentClientsNumber: 10,
  maxConnectionsForOneClient: 10,
}

localServer = webSocket.createWebSocketServer();
localServer.start(config).then((success: boolean) => {
  if (success) {
    console.info('webSocket server start success');
  } else {
    console.error('websocket server start failed');
  }
}).catch((error: BusinessError) => {
  console.error(`Failed to start. Code: ${error.code}, message: ${error.message}`);
});

localServer.stop().then((success: boolean) => {
  if (success) {
    console.info('server stop service successfully');
  } else {
    console.error('server stop service failed');
  }
});
```
