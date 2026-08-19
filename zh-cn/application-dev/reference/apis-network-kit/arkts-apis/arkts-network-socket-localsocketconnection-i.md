# LocalSocketConnection

LocalSocketConnection连接，即LocalSocket客户端与服务端的会话连接。在调用LocalSocketConnection的方法前，需要先获取LocalSocketConnection对象。 > **说明：** > > 客户端与服务端成功建立连接后，才能通过返回的LocalSocketConnection对象调用相应的接口。

**起始版本：** 11

<!--Device-socket-export interface LocalSocketConnection--><!--Device-socket-export interface LocalSocketConnection-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## close

```TypeScript
close(): Promise<void>
```

关闭LocalSocket连接。使用Promise异步回调。

**起始版本：** 11

<!--Device-LocalSocketConnection-close(): Promise<void>--><!--Device-LocalSocketConnection-close(): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2301009](../errorcode-net-socket.md#2301009-错误文件描述符) | Bad file descriptor. |

**示例**

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

获取LocalSocketConnection连接中的本地Socket地址。使用Promise异步回调。

**起始版本：** 12

<!--Device-LocalSocketConnection-getLocalAddress(): Promise<string>--><!--Device-LocalSocketConnection-getLocalAddress(): Promise<string>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | 以Promise形式返回获取本地socket地址的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2301009](../errorcode-net-socket.md#2301009-错误文件描述符) | Bad file descriptor. |
| [2303188](../errorcode-net-socket.md#2303188-非套接字的套接字操作) | Socket operation on non-socket. |

**示例**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

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
getSocketFd(): Promise<int>
```

获取LocalSocketConnection连接的文件描述符。使用Promise异步回调。 > **说明：** > > - 成功建立连接后，才可调用此方法。 > > - 连接断开、Socket已关闭（如调用close后）等异常情况下调用本接口会返回-1。 > > - 文件描述符的生命周期由系统管理，应用可以通过[close](arkts-network-socket-localsocket-i.md#close)方法关闭Socket连接，避免直接操作文件描述符进行关闭。

**起始版本：** 23

<!--Device-LocalSocketConnection-getSocketFd(): Promise<int>--><!--Device-LocalSocketConnection-getSocketFd(): Promise<int>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | Promise对象，返回Socket的文件描述符。 |

**示例**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

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
    console.info(`Socket FD：${fd}`);
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

## off('close')

```TypeScript
off(type: 'close', callback?: Callback<void>): void
```

取消订阅LocalSocketConnection的关闭事件。使用callback异步回调。

**起始版本：** 11

<!--Device-LocalSocketConnection-off(type: 'close', callback?: Callback<void>): void--><!--Device-LocalSocketConnection-off(type: 'close', callback?: Callback<void>): void-End-->

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

let server: socket.LocalSocketServer = socket.constructLocalSocketServerInstance();
let callback = () => {
  console.info("on close success");
}
server.on('connect', (connection: socket.LocalSocketConnection) => {
  connection.on('close', callback);
  // 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。
  connection.off('close', callback);
  connection.off('close');
});
```

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

取消订阅LocalSocketConnection连接的error事件。使用callback异步回调。

**起始版本：** 11

<!--Device-LocalSocketConnection-off(type: 'error', callback?: ErrorCallback): void--><!--Device-LocalSocketConnection-off(type: 'error', callback?: ErrorCallback): void-End-->

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

let callback = (err: Object) => {
  console.error("on error, err: " + JSON.stringify(err));
}
let server: socket.LocalSocketServer = socket.constructLocalSocketServerInstance();
server.on('connect', (connection: socket.LocalSocketConnection) => {
  connection.on('error', callback);
  // 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。
  connection.off('error', callback);
  connection.off('error');
});
```

## off('message')

```TypeScript
off(type: 'message', callback?: Callback<LocalSocketMessageInfo>): void
```

取消订阅LocalSocketConnection连接的接收消息事件。使用callback异步回调。

**起始版本：** 11

<!--Device-LocalSocketConnection-off(type: 'message', callback?: Callback<LocalSocketMessageInfo>): void--><!--Device-LocalSocketConnection-off(type: 'message', callback?: Callback<LocalSocketMessageInfo>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'message' | 是 | 取消订阅的事件类型。'message'：接收消息事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[LocalSocketMessageInfo](arkts-network-socket-localsocketmessageinfo-i.md)&gt; | 否 | 回调函数。可以指定传入on中的callback取消对应的订阅，也可以不指定callback清空所有订阅。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

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
  // 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。
  connection.off('message', callback);
  connection.off('message');
});
```

## on('close')

```TypeScript
on(type: 'close', callback: Callback<void>): void
```

订阅LocalSocketConnection的关闭事件。使用callback异步回调。

**起始版本：** 11

<!--Device-LocalSocketConnection-on(type: 'close', callback: Callback<void>): void--><!--Device-LocalSocketConnection-on(type: 'close', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'close' | 是 | 订阅的事件类型。'close'：关闭事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | 以callback的形式异步返回会话关闭的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

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

订阅LocalSocketConnection连接的error事件。使用callback异步回调。

**起始版本：** 11

<!--Device-LocalSocketConnection-on(type: 'error', callback: ErrorCallback): void--><!--Device-LocalSocketConnection-on(type: 'error', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 订阅的事件类型。'error'：error事件。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-errorcallback-t.md) | 是 | 以callback的形式异步返回出现错误的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';

let server: socket.LocalSocketServer = socket.constructLocalSocketServerInstance();
server.on('connect', (connection: socket.LocalSocketConnection) => {
  connection.on('error', (err: Object) => {
    console.error("on error, err:" + JSON.stringify(err))
  });
});
```

## on('message')

```TypeScript
on(type: 'message', callback: Callback<LocalSocketMessageInfo>): void
```

订阅LocalSocketConnection连接的接收消息事件。使用callback异步回调。

**起始版本：** 11

<!--Device-LocalSocketConnection-on(type: 'message', callback: Callback<LocalSocketMessageInfo>): void--><!--Device-LocalSocketConnection-on(type: 'message', callback: Callback<LocalSocketMessageInfo>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'message' | 是 | 订阅的事件类型。'message'：接收消息事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[LocalSocketMessageInfo](arkts-network-socket-localsocketmessageinfo-i.md)&gt; | 是 | 以callback的形式异步返回接收到的来自客户端的消息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

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

## send

```TypeScript
send(options: LocalSendOptions): Promise<void>
```

通过LocalSocketConnection连接对象发送数据。使用Promise异步回调。 > **说明：** > > 服务端与客户端建立连接后，服务端通过connect事件回调得到LocalSocketConnection连接对象后，才可使用连接对象调用此方法。

**起始版本：** 11

<!--Device-LocalSocketConnection-send(options: LocalSendOptions): Promise<void>--><!--Device-LocalSocketConnection-send(options: LocalSendOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [LocalSendOptions](arkts-network-socket-localsendoptions-i.md) | 是 | LocalSocketConnection发送请求的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 2301011 | Operation would block. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

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
clientId: int
```

客户端与服务端建立的会话连接的id。

**类型：** int

**起始版本：** 11

<!--Device-LocalSocketConnection-clientId: int--><!--Device-LocalSocketConnection-clientId: int-End-->

**系统能力：** SystemCapability.Communication.NetStack

