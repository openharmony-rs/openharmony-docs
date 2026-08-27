# WebSocketServer

在调用WebSocketServer方法前，需要先通过[webSocket.createWebSocketServer](arkts-network-websocket-createwebsocketserver-f.md)创建一个 WebSocketServer。

**起始版本：** 19

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
```

## close

```TypeScript
close(connection: WebSocketConnection, options?: webSocket.WebSocketCloseOptions): Promise<boolean>
```

关闭指定websocket连接。使用Promise异步回调。

**起始版本：** 19

**需要权限：** ohos.permission.INTERNET

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| connection | [WebSocketConnection](arkts-network-websocket-websocketconnection-i.md) | 是 | 客户端信息，包括客户端的ip地址和端口号port。 |
| options | [webSocket.WebSocketCloseOptions](arkts-network-websocket-websocketcloseoptions-i.md) | 否 | 关闭WebSocket连接时，可选参数的类型和说明。    - 错误码默认：200。原因值默认：Websocket connect failed。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;boolean & gt; | promise对象。返回true表示关闭请求创建成功；返回false表示关闭请求创建失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| 2302006 | websocket connection does not exist. |

**示例**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let localServer: webSocket.WebSocketServer;
let config: webSocket.WebSocketServerConfig = {
  serverPort: 8080, // 监听端口
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

获取与服务端连接的所有客户端信息。

> **说明：**
> 
> 该接口为异步调用，返回结果需通过await关键字等待异步操作完成，以确保正确获取到所有客户端连接信息。

**起始版本：** 19

**需要权限：** ohos.permission.INTERNET

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WebSocketConnection](arkts-network-websocket-websocketconnection-i.md)[] | an array consists connections from all clients. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let connections: webSocket.WebSocketConnection[] = [];
let localServer: webSocket.WebSocketServer;
let config: webSocket.WebSocketServerConfig = {
  serverPort: 8080, // 监听端口
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

取消订阅WebSocketServer的连接事件（客户端与服务端建链成功），使用callback异步回调。

> **说明：**
> 
> 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。

**起始版本：** 19

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'connect' | 是 | 事件回调类型，支持的事件为'connect'，当offconnect()调用完成，取消监听连接事件成功。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[WebSocketConnection](arkts-network-websocket-websocketconnection-i.md)&gt; | 否 | 回调函数。连接的客户端信息。 |

**示例**

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

取消订阅WebSocketServer的接收到客户端消息事件，使用callback异步回调。

> **说明：**
> 
> 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。

**起始版本：** 19

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'messageReceive' | 是 | 事件回调类型，支持的事件为'messageReceive'，当offmessageReceive()调用完成，取消订阅接收客户端消息成功。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[WebSocketMessage](arkts-network-websocket-websocketmessage-i.md)&gt; | 否 | 从指定客户端接收到的消息，包括客户端的信息和数据。    - clientconnection：客户端信息。    - data：客户端发送的消息。 |

**示例**

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

取消订阅WebSocketServer的关闭事件，使用callback异步回调。

> **说明：**
> 
> 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。

**起始版本：** 19

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'close' | 是 | 事件回调类型，支持的事件为'close'，当offclose()调用完成，取消订阅连接关闭事件成功。 |
| callback | [ClientConnectionCloseCallback](arkts-network-websocket-clientconnectionclosecallback-t.md) | 否 | 回调函数。 close：close错误码；reason：错误码说明。 |

**示例**

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

取消订阅WebSocketServer的Error事件，使用callback异步回调。

> **说明：**
> 
> 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。

**起始版本：** 19

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 事件回调类型，支持的事件为'error'，当offerror()调用完成，取消订阅error事件成功。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 否 | 回调函数。默认值：200。 |

**示例**

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

订阅WebSocketServer的连接事件（客户端与服务端建链成功），使用callback异步回调。

**起始版本：** 19

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'connect' | 是 | 事件回调类型，支持的事件为'connect'，当onconnect()调用完成，客户端与服务端建链成功。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[WebSocketConnection](arkts-network-websocket-websocketconnection-i.md)&gt; | 是 | 回调函数。连接的客户端信息。 |

**示例**

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

订阅WebSocketServer的接收客户端消息的事件，使用callback异步回调。

**起始版本：** 19

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'messageReceive' | 是 | 事件回调类型，支持的事件为'messageReceive'，当onmessageReceive()调用完成，接收到客户端消息成功。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[WebSocketMessage](arkts-network-websocket-websocketmessage-i.md)&gt; | 是 | 回调函数。 clientconnection:客户端信息，data:客户端发送的数据消息。 |

**示例**

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

订阅WebSocketServer的关闭事件，使用callback异步回调。

**起始版本：** 19

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'close' | 是 | 事件回调类型，支持的事件为'close'，当onclose()调用完成，连接关闭成功。 |
| callback | [ClientConnectionCloseCallback](arkts-network-websocket-clientconnectionclosecallback-t.md) | 是 | 回调函数。 close：close错误码；reason：错误码说明。 |

**示例**

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

订阅WebSocketServer的Error事件，使用callback异步回调。

**起始版本：** 19

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 事件回调类型，支持的事件为'error'，当onerror()调用完成，error事件发生。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 是 | 回调函数。 |

**示例**

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

通过WebSocket连接发送数据。使用Promise异步回调。

> **说明：**
> 
> send接口必须在监听到connect事件后才可以调用。

**起始版本：** 19

**需要权限：** ohos.permission.INTERNET

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string \| ArrayBuffer | 是 | 服务端发送消息的数据，同时支持string（字符串）和ArrayBuffer（二进制）类型。最大支持发送5242864字节数据(即5 * 1024   * 1024 - 16)，超过该大小会返回401错误码。 |
| connection | [WebSocketConnection](arkts-network-websocket-websocketconnection-i.md) | 是 | 发送的客户端信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;boolean & gt; | promise对象。返回true表示发送请求创建成功；返回false表示发送请求创建失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| 2302006 | websocket connection does not exist. |

**示例**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let localServer: webSocket.WebSocketServer;
let config: webSocket.WebSocketServerConfig = {
  serverPort: 8080, // 监听端口
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
  // 当收到on('connect')事件时，可以通过send()方法与客户端进行通信
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

配置config参数，启动服务端service。使用Promise异步回调。

> **说明：**
> 
> 在多次调用该接口时，应避免监听同一端口。

**起始版本：** 19

**需要权限：** ohos.permission.INTERNET

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [WebSocketServerConfig](arkts-network-websocket-websocketserverconfig-i.md) | 是 | 启动websocketServer服务器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;boolean & gt; | promise对象。返回true表示服务器启动成功；返回false表示服务启动失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2302002](../errorcode-net-webSocket.md#2302002-websocket-证书不存在) | Websocket certificate file does not exist. |
| [2302004](../errorcode-net-webSocket.md#2302004-websocketserver-无法在指定的nic网络接口上进行网络监听) | Can't listen on the given NIC. |
| [2302005](../errorcode-net-webSocket.md#2302005-websocketserver-无法在指定的端口上进行网络监听) | Can't listen on the given Port. |
| [2302999](../errorcode-net-webSocket.md#2302999-内部错误) | Websocket other unknown error. |
| [2302007](../errorcode-net-webSocket.md#2302007-websocketserver当前监听的端口已被占用) | Websocket port already occupied.<br>**适用版本：** 24+ |

**示例**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let localServer: webSocket.WebSocketServer;
let config: webSocket.WebSocketServerConfig = {
  serverPort: 8080, // 监听端口
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

停止服务端服务。使用Promise异步回调。

**起始版本：** 19

**需要权限：** ohos.permission.INTERNET

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;boolean & gt; | promise对象。返回true表示停止服务端service请求创建成功；返回false表示停止服务端service请求创建失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let localServer: webSocket.WebSocketServer;
let config: webSocket.WebSocketServerConfig = {
  serverPort: 8080, // 监听端口
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
