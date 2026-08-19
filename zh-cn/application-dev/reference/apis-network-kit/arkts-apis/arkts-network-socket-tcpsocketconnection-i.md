# TCPSocketConnection

TCPSocketConnection连接，即TCPSocket客户端与服务端的连接。在调用TCPSocketConnection的方法前，需要先获取TCPSocketConnection对象。 > **说明：** > > 客户端与服务端成功建立连接后，才能通过返回的TCPSocketConnection对象调用相应的接口。

**起始版本：** 10

<!--Device-socket-export interface TCPSocketConnection--><!--Device-socket-export interface TCPSocketConnection-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## close

```TypeScript
close(callback: AsyncCallback<void>): void
```

关闭一个与TCPSocket建立的连接。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.INTERNET

<!--Device-TCPSocketConnection-close(callback: AsyncCallback<void>): void--><!--Device-TCPSocketConnection-close(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。失败时返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcpServer: socket.TCPSocketServer = socket.constructTCPSocketServerInstance();

tcpServer.on('connect', (client: socket.TCPSocketConnection) => {
  client.close((err: BusinessError) => {
    if (err) {
      console.error('close fail');
      return;
    }
    console.info('close success');
  });
});
```

## close

```TypeScript
close(): Promise<void>
```

关闭一个与TCPSocket建立的连接。使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.INTERNET

<!--Device-TCPSocketConnection-close(): Promise<void>--><!--Device-TCPSocketConnection-close(): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcpServer: socket.TCPSocketServer = socket.constructTCPSocketServerInstance();
tcpServer.on('connect', (client: socket.TCPSocketConnection) => {
  client.close().then(() => {
    console.info('close success');
  }).catch((err: BusinessError) => {
    console.error('close fail');
  });
});
```

## getLocalAddress

```TypeScript
getLocalAddress(): Promise<NetAddress>
```

获取TCPSocketConnection连接的本地Socket地址。使用Promise异步回调。

**起始版本：** 12

<!--Device-TCPSocketConnection-getLocalAddress(): Promise<NetAddress>--><!--Device-TCPSocketConnection-getLocalAddress(): Promise<NetAddress>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;NetAddress&gt; | 以Promise形式返回获取本地socket地址的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2301009](../errorcode-net-socket.md#2301009-错误文件描述符) | Bad file descriptor. |
| [2303188](../errorcode-net-socket.md#2303188-非套接字的套接字操作) | Socket operation on non-socket. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcpServer: socket.TCPSocketServer = socket.constructTCPSocketServerInstance();
let listenAddr: socket.NetAddress = {
  address: "192.168.xx.xx",
  port: 8080,
  family: 1
}
tcpServer.listen(listenAddr, (err: BusinessError) => {
  let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
  let netAddress: socket.NetAddress = {
    address: "192.168.xx.xx",
    port: 8080
  }
  let options: socket.TCPConnectOptions = {
    address: netAddress,
    timeout: 6000
  }
  tcp.connect(options, (err: BusinessError) => {
    if (err) {
      console.error('connect fail');
      return;
    }
    console.info('connect success!');
  })
  tcpServer.on('connect', (client: socket.TCPSocketConnection) => {
    client.getLocalAddress().then((localAddress: socket.NetAddress) => {
      console.info("Family IP Port: " + JSON.stringify(localAddress));
    }).catch((err: BusinessError) => {
      console.error('Error:' + JSON.stringify(err));
    });
  })
})
```

## getRemoteAddress

```TypeScript
getRemoteAddress(callback: AsyncCallback<NetAddress>): void
```

获取对端Socket地址。使用callback异步回调。 > **说明：** > > 与客户端建立连接后，才可调用此方法。

**起始版本：** 10

**需要权限：** ohos.permission.INTERNET

<!--Device-TCPSocketConnection-getRemoteAddress(callback: AsyncCallback<NetAddress>): void--><!--Device-TCPSocketConnection-getRemoteAddress(callback: AsyncCallback<NetAddress>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;NetAddress&gt; | 是 | 回调函数。失败时返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2303188](../errorcode-net-socket.md#2303188-非套接字的套接字操作) | Socket operation on non-socket. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcpServer: socket.TCPSocketServer = socket.constructTCPSocketServerInstance();
tcpServer.on('connect', (client: socket.TCPSocketConnection) => {
  client.getRemoteAddress((err: BusinessError, data: socket.NetAddress) => {
    if (err) {
      console.error('getRemoteAddress fail');
      return;
    }
    console.info('getRemoteAddress success:' + JSON.stringify(data));
  });
});
```

## getRemoteAddress

```TypeScript
getRemoteAddress(): Promise<NetAddress>
```

获取对端Socket地址。使用Promise异步回调。 > **说明：** > > 与客户端建立连接后，才可调用此方法。

**起始版本：** 10

**需要权限：** ohos.permission.INTERNET

<!--Device-TCPSocketConnection-getRemoteAddress(): Promise<NetAddress>--><!--Device-TCPSocketConnection-getRemoteAddress(): Promise<NetAddress>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;NetAddress&gt; | 以Promise形式返回获取对端socket地址的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2303188](../errorcode-net-socket.md#2303188-非套接字的套接字操作) | Socket operation on non-socket. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcpServer: socket.TCPSocketServer = socket.constructTCPSocketServerInstance();
tcpServer.on('connect', (client: socket.TCPSocketConnection) => {
  client.getRemoteAddress().then(() => {
    console.info('getRemoteAddress success');
  }).catch((err: BusinessError) => {
    console.error('getRemoteAddress fail');
  });
});
```

## getSocketFd

```TypeScript
getSocketFd(): Promise<int>
```

获取TCPSocketConnection连接的文件描述符。使用Promise异步回调。 > **说明：** > > - 与客户端建立连接后，才可调用此方法。 > > - 连接断开、Socket已关闭（如调用close后）等异常情况下调用本接口会返回-1。 > > - 文件描述符的生命周期由系统管理，应用可以通过[close](#close)方法关闭 > Socket连接，避免直接操作文件描述符进行关闭。

**起始版本：** 23

**需要权限：** ohos.permission.INTERNET

<!--Device-TCPSocketConnection-getSocketFd(): Promise<int>--><!--Device-TCPSocketConnection-getSocketFd(): Promise<int>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | Promise对象，返回Socket的文件描述符。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcpServer: socket.TCPSocketServer = socket.constructTCPSocketServerInstance();
let listenAddr: socket.NetAddress = {
  address: "192.168.xx.xx",
  port: 8080,
  family: 1
}
tcpServer.listen(listenAddr, (err: BusinessError) => {
  tcpServer.on('connect', (client: socket.TCPSocketConnection) => {
    client.getSocketFd().then((fd: number) => {
      console.info(`Socket FD：${fd}`);
    }).catch((err: BusinessError) => {
      console.error(`getSocketFd fail: ${err.message}, errorCode: ${err.code}`);
    });
  })
}).catch((err: BusinessError) => {
  console.error('listen fail');
});
```

## off('close')

```TypeScript
off(type: 'close', callback?: Callback<void>): void
```

取消订阅TCPSocketConnection的关闭事件。使用callback异步回调。

**起始版本：** 10

<!--Device-TCPSocketConnection-off(type: 'close', callback?: Callback<void>): void--><!--Device-TCPSocketConnection-off(type: 'close', callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'close' | 是 | 取消订阅的事件类型。'close'：关闭事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | 回调函数。可以指定传入on中的callback取消对应的订阅，也可以不指定callback清空所有订阅。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';

let tcpServer: socket.TCPSocketServer = socket.constructTCPSocketServerInstance();
let callback = () => {
  console.info("on close success");
}
tcpServer.on('connect', (client: socket.TCPSocketConnection) => {
  client.on('close', callback);
  // 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。
  client.off('close', callback);
  client.off('close');
});
```

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

取消订阅TCPSocketConnection连接的error事件。使用callback异步回调。

**起始版本：** 10

<!--Device-TCPSocketConnection-off(type: 'error', callback?: ErrorCallback): void--><!--Device-TCPSocketConnection-off(type: 'error', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 取消订阅的事件类型。'error'：error事件。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-errorcallback-t.md) | 否 | 回调函数。可以指定传入on中的callback取消对应的订阅，也可以不指定callback清空所有订阅。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let callback = (err: BusinessError) => {
  console.error("on error, err:" + JSON.stringify(err));
}
let tcpServer: socket.TCPSocketServer = socket.constructTCPSocketServerInstance();
tcpServer.on('connect', (client: socket.TCPSocketConnection) => {
  client.on('error', callback);
  // 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。
  client.off('error', callback);
  client.off('error');
});
```

## off('message')

```TypeScript
off(type: 'message', callback?: Callback<SocketMessageInfo>): void
```

取消订阅TCPSocketConnection连接的接收消息事件。使用callback异步回调。

**起始版本：** 10

<!--Device-TCPSocketConnection-off(type: 'message', callback?: Callback<SocketMessageInfo>): void--><!--Device-TCPSocketConnection-off(type: 'message', callback?: Callback<SocketMessageInfo>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'message' | 是 | 取消订阅的事件类型。'message'：接收消息事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[SocketMessageInfo](arkts-network-socket-socketmessageinfo-i.md)&gt; | 否 | 回调函数。可以指定传入on中的callback取消对应的订阅，也可以不指定callback清空所有订阅。<br>**起始版本：** 11 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcpServer: socket.TCPSocketServer = socket.constructTCPSocketServerInstance();
let callback = (value: socket.SocketMessageInfo) => {
  let messageView = '';
  for (let i: number = 0; i < value.message.byteLength; i++) {
    let uint8Array = new Uint8Array(value.message) 
    let messages = uint8Array[i]
    let message = String.fromCharCode(messages);
    messageView += message;
  }
  console.info('on message message: ' + JSON.stringify(messageView));
  console.info('remoteInfo: ' + JSON.stringify(value.remoteInfo));
}
tcpServer.on('connect', (client: socket.TCPSocketConnection) => {
  client.on('message', callback);
  // 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。
  client.off('message', callback);
  client.off('message');
});
```

## on('close')

```TypeScript
on(type: 'close', callback: Callback<void>): void
```

订阅TCPSocketConnection的关闭事件。使用callback异步回调。

**起始版本：** 10

<!--Device-TCPSocketConnection-on(type: 'close', callback: Callback<void>): void--><!--Device-TCPSocketConnection-on(type: 'close', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'close' | 是 | 订阅的事件类型。'close'：关闭事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | 回调函数。失败时返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcpServer: socket.TCPSocketServer = socket.constructTCPSocketServerInstance();
tcpServer.on('connect', (client: socket.TCPSocketConnection) => {
  client.on('close', () => {
    console.info("on close success")
  });
});
```

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

订阅TCPSocketConnection连接的error事件。使用callback异步回调。

**起始版本：** 10

<!--Device-TCPSocketConnection-on(type: 'error', callback: ErrorCallback): void--><!--Device-TCPSocketConnection-on(type: 'error', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 订阅的事件类型。'error'：error事件。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-errorcallback-t.md) | 是 | 回调函数。失败时返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcpServer: socket.TCPSocketServer = socket.constructTCPSocketServerInstance();
tcpServer.on('connect', (client: socket.TCPSocketConnection) => {
  client.on('error', (err: BusinessError) => {
    console.error("on error, err:" + JSON.stringify(err))
  });
});
```

## on('message')

```TypeScript
on(type: 'message', callback: Callback<SocketMessageInfo>): void
```

订阅TCPSocketConnection连接的接收消息事件。使用callback异步回调。

**起始版本：** 10

<!--Device-TCPSocketConnection-on(type: 'message', callback: Callback<SocketMessageInfo>): void--><!--Device-TCPSocketConnection-on(type: 'message', callback: Callback<SocketMessageInfo>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'message' | 是 | 订阅的事件类型。'message'：接收消息事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[SocketMessageInfo](arkts-network-socket-socketmessageinfo-i.md)&gt; | 是 | 回调函数。失败时返回错误码、错误信息。<br>**起始版本：** 11 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcpServer: socket.TCPSocketServer = socket.constructTCPSocketServerInstance();

tcpServer.on('connect', (client: socket.TCPSocketConnection) => {
  client.on('message', (value: socket.SocketMessageInfo) => {
    let messageView = '';
    let uint8Array = new Uint8Array(value.message); 
    for (let i: number = 0; i < value.message.byteLength; i++) {
      let messages = uint8Array[i];
      let message = String.fromCharCode(messages);
      messageView += message;
    }
    console.info('on message message: ' + JSON.stringify(messageView));
    console.info('remoteInfo: ' + JSON.stringify(value.remoteInfo));
  });
});
```

## send

```TypeScript
send(options: TCPSendOptions, callback: AsyncCallback<void>): void
```

通过TCPSocketConnection连接发送数据。使用callback异步回调。 > **说明：** > > 与客户端建立连接后，才可调用此方法。

**起始版本：** 10

**需要权限：** ohos.permission.INTERNET

<!--Device-TCPSocketConnection-send(options: TCPSendOptions, callback: AsyncCallback<void>): void--><!--Device-TCPSocketConnection-send(options: TCPSendOptions, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TCPSendOptions](arkts-network-socket-tcpsendoptions-i.md) | 是 | TCPSocketConnection发送请求的参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。失败时返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';

let tcpServer: socket.TCPSocketServer = socket.constructTCPSocketServerInstance();

tcpServer.on('connect', (client: socket.TCPSocketConnection) => {
  let tcpSendOption: socket.TCPSendOptions = {
    data: 'Hello, client!'
  }
  client.send(tcpSendOption, () => {
    console.info('send success');
  });
});
```

## send

```TypeScript
send(options: TCPSendOptions): Promise<void>
```

通过TCPSocketConnection连接发送数据。使用Promise异步回调。 > **说明：** > > 与客户端建立连接后，才可调用此方法。

**起始版本：** 10

**需要权限：** ohos.permission.INTERNET

<!--Device-TCPSocketConnection-send(options: TCPSendOptions): Promise<void>--><!--Device-TCPSocketConnection-send(options: TCPSendOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TCPSendOptions](arkts-network-socket-tcpsendoptions-i.md) | 是 | TCPSocketConnection发送请求的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcpServer: socket.TCPSocketServer = socket.constructTCPSocketServerInstance();

tcpServer.on('connect', (client: socket.TCPSocketConnection) => {
  let tcpSendOption: socket.TCPSendOptions = {
    data: 'Hello, client!'
  }
  client.send(tcpSendOption).then(() => {
    console.info('send success');
  }).catch((err: BusinessError) => {
    console.error('send fail');
  });
});
```

## clientId

```TypeScript
clientId: int
```

客户端与TCPSocketServer建立连接的id。

**类型：** int

**起始版本：** 10

<!--Device-TCPSocketConnection-clientId: int--><!--Device-TCPSocketConnection-clientId: int-End-->

**系统能力：** SystemCapability.Communication.NetStack

