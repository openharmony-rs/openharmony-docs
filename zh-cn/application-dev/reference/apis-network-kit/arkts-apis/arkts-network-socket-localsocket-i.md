# LocalSocket

LocalSocket连接。在调用LocalSocket的方法前，需要先通过 [socket.constructLocalSocketInstance](arkts-network-socket-constructlocalsocketinstance-f.md)创建LocalSocket对象。

**起始版本：** 11

<!--Device-socket-export interface LocalSocket--><!--Device-socket-export interface LocalSocket-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## bind

```TypeScript
bind(address: LocalAddress): Promise<void>
```

绑定本地套接字文件的路径。使用Promise异步回调。 > **说明：** > > bind方法可以使客户端确保有个明确的本地套接字路径，显式的绑定一个本地套接字文件。 > > bind方法在本地套接字通信中非必须。

**起始版本：** 11

<!--Device-LocalSocket-bind(address: LocalAddress): Promise<void>--><!--Device-LocalSocket-bind(address: LocalAddress): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| address | [LocalAddress](arkts-network-socket-localaddress-i.md) | 是 | 本端地址信息，参考[LocalAddress](arkts-network-socket-localaddress-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2301013](../errorcode-net-socket.md#2301013-权限不足) | Insufficient permissions. |
| 2301098 | Address already in use. |
| 2301022 | Invalid argument. |

**示例**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { socket } from '@kit.NetworkKit';
import { common } from '@kit.AbilityKit';

let client: socket.LocalSocket = socket.constructLocalSocketInstance()
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let sandboxPath: string = context.filesDir + '/testSocket';
let address : socket.LocalAddress = {
  address: sandboxPath
}
client.bind(address).then(() => {
  console.info('bind success')
}).catch((err: Object) => {
  console.error('failed to bind: ' + JSON.stringify(err))
})
```

## close

```TypeScript
close(): Promise<void>
```

关闭LocalSocket连接。使用Promise异步回调。

**起始版本：** 11

<!--Device-LocalSocket-close(): Promise<void>--><!--Device-LocalSocket-close(): Promise<void>-End-->

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

let client: socket.LocalSocket = socket.constructLocalSocketInstance();

client.close().then(() => {
  console.info('close success');
}).catch((err: Object) => {
  console.error('close fail: ' + JSON.stringify(err));
});
```

## connect

```TypeScript
connect(options: LocalConnectOptions): Promise<void>
```

连接到指定的套接字文件。使用Promise异步回调。 > **说明：** > > 在没有执行localsocket.bind的情况下，也可以直接调用该接口完成与LocalSocket服务端的连接。

**起始版本：** 11

<!--Device-LocalSocket-connect(options: LocalConnectOptions): Promise<void>--><!--Device-LocalSocket-connect(options: LocalConnectOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [LocalConnectOptions](arkts-network-socket-localconnectoptions-i.md) | 是 | LocalSocket连接的参数，参考 [LocalConnectOptions](arkts-network-socket-localconnectoptions-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 以Promise形式返回LocalSocket连接服务端的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| 2301111 | Connection refused. |
| [2301013](../errorcode-net-socket.md#2301013-权限不足) | Insufficient permissions. |
| 2301099 | Cannot assign requested address. |
| 2301022 | Invalid argument. |

**示例**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { socket } from '@kit.NetworkKit';
import { common } from '@kit.AbilityKit';

let client: socket.LocalSocket = socket.constructLocalSocketInstance();
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let sandboxPath: string = context.filesDir + '/testSocket';
let localAddress : socket.LocalAddress = {
  address: sandboxPath
}
let connectOpt: socket.LocalConnectOptions = {
  address: localAddress,
  timeout: 6000
}
client.connect(connectOpt).then(() => {
  console.info('connect success')
}).catch((err: Object) => {
  console.error('connect fail: ' + JSON.stringify(err));
});
```

## getExtraOptions

```TypeScript
getExtraOptions(): Promise<ExtraOptionsBase>
```

获取LocalSocket的套接字属性。使用Promise异步回调。 > **说明：** > > bind或connect方法调用成功后，才可调用此方法。

**起始版本：** 11

<!--Device-LocalSocket-getExtraOptions(): Promise<ExtraOptionsBase>--><!--Device-LocalSocket-getExtraOptions(): Promise<ExtraOptionsBase>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ExtraOptionsBase](arkts-network-socket-extraoptionsbase-i.md)&gt; | 以Promise形式返回设置LocalSocket套接字的属性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2301009](../errorcode-net-socket.md#2301009-错误文件描述符) | Bad file descriptor. |

**示例**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { socket } from '@kit.NetworkKit';
import { common } from '@kit.AbilityKit';

let client: socket.LocalSocket = socket.constructLocalSocketInstance();
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let sandboxPath: string = context.filesDir + '/testSocket';
let localAddress : socket.LocalAddress = {
  address: sandboxPath
}
let connectOpt: socket.LocalConnectOptions = {
  address: localAddress,
  timeout: 6000
}
client.connect(connectOpt).then(() => {
  console.info('connect success');
  client.getExtraOptions().then((options : socket.ExtraOptionsBase) => {
    console.info('options: ' + JSON.stringify(options));
  }).catch((err: Object) => {
    console.error('setExtraOptions fail: ' + JSON.stringify(err));
  });
}).catch((err: Object) => {
  console.error('connect fail: ' + JSON.stringify(err));
});
```

## getLocalAddress

```TypeScript
getLocalAddress(): Promise<string>
```

获取LocalSocket的本地Socket地址。使用Promise异步回调。 > **说明：** > > bind方法调用成功后，才可调用此方法。

**起始版本：** 12

<!--Device-LocalSocket-getLocalAddress(): Promise<string>--><!--Device-LocalSocket-getLocalAddress(): Promise<string>-End-->

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

let client: socket.LocalSocket = socket.constructLocalSocketInstance();
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let sandboxPath: string = context.filesDir + '/testSocket';
let address : socket.LocalAddress = {
  address: sandboxPath
}
client.bind(address).then(() => {
  console.error('bind success');
  client.getLocalAddress().then((localPath: string) => {
    console.info("SUCCESS " + JSON.stringify(localPath));
  }).catch((err: BusinessError) => {
    console.error("FAIL " + JSON.stringify(err));
  })
}).catch((err: Object) => {
  console.error('failed to bind: ' + JSON.stringify(err));
})
```

## getSocketFd

```TypeScript
getSocketFd(): Promise<int>
```

获取LocalSocket的文件描述符。使用Promise异步回调。 > **说明：** > > - bind或connect方法调用成功后，才可调用此方法。 > > - 获取由系统内核分配的唯一文件描述符，用于标识当前使用的套接字。 > > - 文件描述符的生命周期由系统管理，应用可以通过[close](#close)方法关闭Socket连接，避免直接操作文件描述符进行关闭。

**起始版本：** 11

<!--Device-LocalSocket-getSocketFd(): Promise<int>--><!--Device-LocalSocket-getSocketFd(): Promise<int>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | 以Promise形式返回socket的文件描述符。 |

**示例**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { socket } from '@kit.NetworkKit';
import { common } from '@kit.AbilityKit';

let client: socket.LocalSocket = socket.constructLocalSocketInstance();
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let sandboxPath: string = context.filesDir + '/testSocket';
let localAddress : socket.LocalAddress = {
  address: sandboxPath
}
let connectOpt: socket.LocalConnectOptions = {
  address: localAddress,
  timeout: 6000
}
client.connect(connectOpt).then(() => {
  console.info('connect ok')
}).catch((err: Object) => {
  console.error('connect fail: ' + JSON.stringify(err))
})
client.getSocketFd().then((data: number) => {
  console.info("fd: " + data);
}).catch((err: Object) => {
  console.error("getSocketFd failed: " + JSON.stringify(err));
})
```

## getState

```TypeScript
getState(): Promise<SocketStateBase>
```

获取LocalSocket状态。使用Promise异步回调。 > **说明：** > > bind或connect方法调用成功后，才可调用此方法。

**起始版本：** 11

<!--Device-LocalSocket-getState(): Promise<SocketStateBase>--><!--Device-LocalSocket-getState(): Promise<SocketStateBase>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[SocketStateBase](arkts-network-socket-socketstatebase-i.md)&gt; | 以Promise形式返回获取LocalSocket状态的结果。 |

**示例**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { socket } from '@kit.NetworkKit';
import { common } from '@kit.AbilityKit';

let client: socket.LocalSocket = socket.constructLocalSocketInstance();
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let sandboxPath: string = context.filesDir + '/testSocket';
let localAddress : socket.LocalAddress = {
  address: sandboxPath
}
let connectOpt: socket.LocalConnectOptions = {
  address: localAddress,
  timeout: 6000
}
client.connect(connectOpt).then(() => {
  console.info('connect success');
  client.getState().then(() => {
    console.info('getState success');
  }).catch((err: Object) => {
    console.error('getState fail: ' + JSON.stringify(err))
  });
}).catch((err: Object) => {
  console.error('connect fail: ' + JSON.stringify(err));
});
```

## off('close')

```TypeScript
off(type: 'close', callback?: Callback<void>): void
```

取消订阅LocalSocket的关闭事件。使用callback异步回调。

**起始版本：** 11

<!--Device-LocalSocket-off(type: 'close', callback?: Callback<void>): void--><!--Device-LocalSocket-off(type: 'close', callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'close' | 是 | 取消订阅的事件类型。'close'：LocalSocket的关闭事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | 回调函数。可以指定传入on中的callback取消对应的订阅，也可以不指定callback清空所有订阅。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';

let client: socket.LocalSocket = socket.constructLocalSocketInstance();
let callback = () => {
  console.info("on close success");
}
client.on('close', callback);
// 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。
client.off('close', callback);
client.off('close');
```

## off('connect')

```TypeScript
off(type: 'connect', callback?: Callback<void>): void
```

取消订阅LocalSocket的连接事件。使用callback异步回调。

**起始版本：** 11

<!--Device-LocalSocket-off(type: 'connect', callback?: Callback<void>): void--><!--Device-LocalSocket-off(type: 'connect', callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'connect' | 是 | 取消订阅的事件类型。'connect'：LocalSocket的connect事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | 回调函数。可以指定传入on中的callback取消对应的订阅，也可以不指定callback清空所有订阅。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';

let client: socket.LocalSocket = socket.constructLocalSocketInstance();
let callback = () => {
  console.info("on connect success");
}
client.on('connect', callback);
// 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。
client.off('connect', callback);
client.off('connect');
```

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

取消订阅LocalSocket连接的error事件。使用callback异步回调。

**起始版本：** 11

<!--Device-LocalSocket-off(type: 'error', callback?: ErrorCallback): void--><!--Device-LocalSocket-off(type: 'error', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 取消订阅的事件类型。'error'：LocalSocket的error事件。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-errorcallback-t.md) | 否 | 回调函数。可以指定传入on中的callback取消对应的订阅，也可以不指定callback清空所有订阅。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';

let client: socket.LocalSocket = socket.constructLocalSocketInstance();
let callback = (err: Object) => {
  console.error("on error, err:" + JSON.stringify(err));
}
client.on('error', callback);
// 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。
client.off('error', callback);
client.off('error');
```

## off('message')

```TypeScript
off(type: 'message', callback?: Callback<LocalSocketMessageInfo>): void
```

取消订阅LocalSocket连接的接收消息事件。使用callback异步回调。

**起始版本：** 11

<!--Device-LocalSocket-off(type: 'message', callback?: Callback<LocalSocketMessageInfo>): void--><!--Device-LocalSocket-off(type: 'message', callback?: Callback<LocalSocketMessageInfo>): void-End-->

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

let client: socket.LocalSocket = socket.constructLocalSocketInstance();
let messageView = '';
let callback = (value: socket.LocalSocketMessageInfo) => {
  const uintArray = new Uint8Array(value.message)
  let messageView = '';
  for (let i = 0; i < uintArray.length; i++) {
    messageView += String.fromCharCode(uintArray[i]);
  }
  console.info('total: ' + JSON.stringify(value));
  console.info('message information: ' + messageView);
}
client.on('message', callback);
client.off('message');
```

## on('close')

```TypeScript
on(type: 'close', callback: Callback<void>): void
```

订阅LocalSocket的关闭事件。使用callback异步回调。

**起始版本：** 11

<!--Device-LocalSocket-on(type: 'close', callback: Callback<void>): void--><!--Device-LocalSocket-on(type: 'close', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'close' | 是 | 订阅LocalSocket的关闭事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | 以callback的形式异步返回关闭localsocket的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';

let client: socket.LocalSocket = socket.constructLocalSocketInstance();
let callback = () => {
  console.info("on close success");
}
client.on('close', callback);
```

## on('connect')

```TypeScript
on(type: 'connect', callback: Callback<void>): void
```

订阅LocalSocket的连接事件。使用callback异步回调。

**起始版本：** 11

<!--Device-LocalSocket-on(type: 'connect', callback: Callback<void>): void--><!--Device-LocalSocket-on(type: 'connect', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'connect' | 是 | 订阅的事件类型。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | 以callback的形式异步返回与服务端连接的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';

let client: socket.LocalSocket = socket.constructLocalSocketInstance();
client.on('connect', () => {
  console.info("on connect success")
});
```

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

订阅LocalSocket连接的error事件。使用callback异步回调。

**起始版本：** 11

<!--Device-LocalSocket-on(type: 'error', callback: ErrorCallback): void--><!--Device-LocalSocket-on(type: 'error', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 订阅LocalSocket的error事件。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-errorcallback-t.md) | 是 | 以callback的形式异步返回出现错误的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';

let client: socket.LocalSocket = socket.constructLocalSocketInstance();
client.on('error', (err: Object) => {
  console.error("on error, err:" + JSON.stringify(err))
});
```

## on('message')

```TypeScript
on(type: 'message', callback: Callback<LocalSocketMessageInfo>): void
```

订阅LocalSocket连接的接收消息事件。使用callback异步回调。

**起始版本：** 11

<!--Device-LocalSocket-on(type: 'message', callback: Callback<LocalSocketMessageInfo>): void--><!--Device-LocalSocket-on(type: 'message', callback: Callback<LocalSocketMessageInfo>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'message' | 是 | 订阅的事件类型。'message'：接收消息事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[LocalSocketMessageInfo](arkts-network-socket-localsocketmessageinfo-i.md)&gt; | 是 | 以callback的形式异步返回接收的消息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';

let client: socket.LocalSocket = socket.constructLocalSocketInstance();
client.on('message', (value: socket.LocalSocketMessageInfo) => {
  const uintArray = new Uint8Array(value.message)
  let messageView = '';
  for (let i = 0; i < uintArray.length; i++) {
    messageView += String.fromCharCode(uintArray[i]);
  }
  console.info('total: ' + JSON.stringify(value));
  console.info('message information: ' + messageView);
});
```

## send

```TypeScript
send(options: LocalSendOptions): Promise<void>
```

通过LocalSocket连接发送数据。使用Promise异步回调。 > **说明：** > > connect方法调用成功后，才可调用此方法。

**起始版本：** 11

<!--Device-LocalSocket-send(options: LocalSendOptions): Promise<void>--><!--Device-LocalSocket-send(options: LocalSendOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [LocalSendOptions](arkts-network-socket-localsendoptions-i.md) | 是 | LocalSocket发送请求的参数，参考[LocalSendOptions](arkts-network-socket-localsendoptions-i.md)。 |

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

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { socket } from '@kit.NetworkKit';
import { common } from '@kit.AbilityKit';

let client: socket.LocalSocket = socket.constructLocalSocketInstance()
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let sandboxPath: string = context.filesDir + '/testSocket';
let localAddress : socket.LocalAddress = {
  address: sandboxPath
}
let connectOpt: socket.LocalConnectOptions = {
  address: localAddress,
  timeout: 6000
}
client.connect(connectOpt).then(() => {
  console.info('connect success')
}).catch((err: Object) => {
  console.error('connect failed: ' + JSON.stringify(err))
})
let sendOpt: socket.LocalSendOptions = {
  data: 'Hello world!'
}
client.send(sendOpt).then(() => {
  console.info('send success')
}).catch((err: Object) => {
  console.error('send fail: ' + JSON.stringify(err))
})
```

## setExtraOptions

```TypeScript
setExtraOptions(options: ExtraOptionsBase): Promise<void>
```

设置LocalSocket的套接字属性。使用Promise异步回调。 > **说明：** > > bind或connect方法调用成功后，才可调用此方法。

**起始版本：** 11

<!--Device-LocalSocket-setExtraOptions(options: ExtraOptionsBase): Promise<void>--><!--Device-LocalSocket-setExtraOptions(options: ExtraOptionsBase): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ExtraOptionsBase](arkts-network-socket-extraoptionsbase-i.md) | 是 | LocalSocket连接的其他属性，参考[ExtraOptionsBase](arkts-network-socket-extraoptionsbase-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 以Promise形式返回设置LocalSocket套接字属性的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2301009](../errorcode-net-socket.md#2301009-错误文件描述符) | Bad file descriptor. |

**示例**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { socket } from '@kit.NetworkKit';
import { common } from '@kit.AbilityKit';

let client: socket.LocalSocket = socket.constructLocalSocketInstance();
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let sandboxPath: string = context.filesDir + '/testSocket';
let localAddress : socket.LocalAddress = {
  address: sandboxPath
}
let connectOpt: socket.LocalConnectOptions = {
  address: localAddress,
  timeout: 6000
}
client.connect(connectOpt).then(() => {
  console.info('connect success');
  let options: socket.ExtraOptionsBase = {
    receiveBufferSize: 8192,
    sendBufferSize: 8192,
    socketTimeout: 3000
  }
  client.setExtraOptions(options).then(() => {
    console.info('setExtraOptions success');
  }).catch((err: Object) => {
    console.error('setExtraOptions fail: ' + JSON.stringify(err));
  });
}).catch((err: Object) => {
  console.error('connect fail: ' + JSON.stringify(err));
});
```

