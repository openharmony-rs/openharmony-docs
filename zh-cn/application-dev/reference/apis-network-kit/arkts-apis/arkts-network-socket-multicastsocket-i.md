# MulticastSocket

MulticastSocket连接。在调用MulticastSocket的方法前，需要先通过 [socket.constructMulticastSocketInstance](arkts-network-socket-constructmulticastsocketinstance-f.md)创建MulticastSocket对象。

**继承/实现关系：** MulticastSocket extends [UDPSocket](arkts-network-socket-udpsocket-i.md)

**起始版本：** 11

<!--Device-socket-export interface MulticastSocket--><!--Device-socket-export interface MulticastSocket-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## addMembership

```TypeScript
addMembership(multicastAddress: NetAddress, callback: AsyncCallback<void>): void
```

加入多播组。使用callback异步回调。 > **说明：** > > 多播使用的IP地址属于特定的范围（例如224.0.0.0到239.255.255.255）。 > > 加入多播组后，既可以是发送端，也可以是接收端，相互之间以广播的形式传递数据，不区分客户端或服务端。

**起始版本：** 11

**需要权限：** ohos.permission.INTERNET

<!--Device-MulticastSocket-addMembership(multicastAddress: NetAddress, callback: AsyncCallback<void>): void--><!--Device-MulticastSocket-addMembership(multicastAddress: NetAddress, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| multicastAddress | NetAddress | 是 | 目标地址信息，参考 NetAddress。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| 2301088 | Not a socket. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| 2301098 | Address in use. |
| 2301022 | Invalid argument. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';

let multicast: socket.MulticastSocket = socket.constructMulticastSocketInstance();
let addr: socket.NetAddress = {
  address: '239.255.0.1',
  port: 8080
}
multicast.addMembership(addr, (err: Object) => {
  if (err) {
    console.error('add membership fail, err: ' + JSON.stringify(err));
    return;
  }
  console.info('add membership success');
})
```

## addMembership

```TypeScript
addMembership(multicastAddress: NetAddress): Promise<void>
```

加入多播组。使用Promise异步回调。 > **说明：** > > 多播使用的IP地址属于特定的范围（例如224.0.0.0到239.255.255.255）。 > > 加入多播组后，既可以是发送端，也可以是接收端，相互之间以广播的形式传递数据，不区分客户端或服务端。

**起始版本：** 11

**需要权限：** ohos.permission.INTERNET

<!--Device-MulticastSocket-addMembership(multicastAddress: NetAddress): Promise<void>--><!--Device-MulticastSocket-addMembership(multicastAddress: NetAddress): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| multicastAddress | NetAddress | 是 | 目标地址信息，参考 NetAddress。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 以Promise形式返回MulticastSocket加入多播组的行为结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| 2301088 | Not a socket. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| 2301098 | Address in use. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';

let multicast: socket.MulticastSocket = socket.constructMulticastSocketInstance();
let addr: socket.NetAddress = {
  address: '239.255.0.1',
  port: 8080
}
multicast.addMembership(addr).then(() => {
  console.info('addMembership success');
}).catch((err: Object) => {
  console.error('addMembership fail');
});
```

## dropMembership

```TypeScript
dropMembership(multicastAddress: NetAddress, callback: AsyncCallback<void>): void
```

退出多播组。使用callback异步回调。 > **说明：** > > 多播使用的IP地址属于特定的范围（例如224.0.0.0到239.255.255.255）。 > > 从已加入的多播组中退出，必须在加入多播组 > [addMembership](#addmembership) > 之后退出才有效。

**起始版本：** 11

**需要权限：** ohos.permission.INTERNET

<!--Device-MulticastSocket-dropMembership(multicastAddress: NetAddress, callback: AsyncCallback<void>): void--><!--Device-MulticastSocket-dropMembership(multicastAddress: NetAddress, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| multicastAddress | NetAddress | 是 | 目标地址信息，参考 NetAddress。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| 2301088 | Not a socket. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| 2301098 | Address in use. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';

let multicast: socket.MulticastSocket = socket.constructMulticastSocketInstance();
let addr: socket.NetAddress = {
  address: '239.255.0.1',
  port: 8080
}
multicast.dropMembership(addr, (err: Object) => {
  if (err) {
    console.error('drop membership fail, err: ' + JSON.stringify(err));
    return;
  }
  console.info('drop membership success');
})
```

## dropMembership

```TypeScript
dropMembership(multicastAddress: NetAddress): Promise<void>
```

退出多播组。使用Promise异步回调。 > **说明：** > > 多播使用的IP地址属于特定的范围（例如224.0.0.0到239.255.255.255）。 > > 从已加入的多播组中退出，必须在加入多播组 > [addMembership](#addmembership) > 之后退出才有效。

**起始版本：** 11

**需要权限：** ohos.permission.INTERNET

<!--Device-MulticastSocket-dropMembership(multicastAddress: NetAddress): Promise<void>--><!--Device-MulticastSocket-dropMembership(multicastAddress: NetAddress): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| multicastAddress | NetAddress | 是 | 目标地址信息，参考 NetAddress。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 以Promise形式返回MulticastSocket加入多播组的执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| 2301088 | Not a socket. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| 2301098 | Address in use. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';

let multicast: socket.MulticastSocket = socket.constructMulticastSocketInstance();
let addr: socket.NetAddress = {
  address: '239.255.0.1',
  port: 8080
}
multicast.dropMembership(addr).then(() => {
  console.info('drop membership success');
}).catch((err: Object) => {
  console.error('drop membership fail');
});
```

## getLoopbackMode

```TypeScript
getLoopbackMode(callback: AsyncCallback<boolean>): void
```

获取多播通信中的环回模式状态。使用callback异步回调。 > **说明：** > > 用于获取当前环回模式开启或关闭的状态。 > > 如果获取的属性值为 true，表示环回模式是开启的状态，允许主机在本地循环接收自己发送的多播数据包。如果为 false，则表示环回模式是关闭的状态，主机不会接收到自己发送的多播数据包。 > > 在调用 > [addMembership](#addmembership) > 之后，调用此接口才有效。

**起始版本：** 11

<!--Device-MulticastSocket-getLoopbackMode(callback: AsyncCallback<boolean>): void--><!--Device-MulticastSocket-getLoopbackMode(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 回调函数。返回值为环回模式状态，true表示环回模式开启，false表示环回模式关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| 2301088 | Not a socket. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';

let multicast: socket.MulticastSocket = socket.constructMulticastSocketInstance();
multicast.getLoopbackMode((err: Object, value: Boolean) => {
  if (err) {
    console.error('get loopback mode fail, err: ' + JSON.stringify(err));
    return;
  }
  console.info('get loopback mode success, value: ' + JSON.stringify(value));
})
```

## getLoopbackMode

```TypeScript
getLoopbackMode(): Promise<boolean>
```

获取多播通信中的环回模式状态。使用Promise异步回调。 > **说明：** > > 用于获取当前环回模式开启或关闭的状态。 > > 如果获取的属性值为 true，表示环回模式是开启的状态，允许主机在本地循环接收自己发送的多播数据包。如果为 false，则表示环回模式是关闭的状态，主机不会接收到自己发送的多播数据包。 > > 在调用 > [addMembership](#addmembership) > 之后，调用此接口才有效。

**起始版本：** 11

<!--Device-MulticastSocket-getLoopbackMode(): Promise<boolean>--><!--Device-MulticastSocket-getLoopbackMode(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示环回模式开启，返回false表示环回模式关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| 2301088 | Not a socket. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';

let multicast: socket.MulticastSocket = socket.constructMulticastSocketInstance();
multicast.getLoopbackMode().then((value: Boolean) => {
  console.info('loopback mode: ', JSON.stringify(value));
}).catch((err: Object) => {
  console.error('get loopback mode failed');
});
```

## getMulticastTTL

```TypeScript
getMulticastTTL(callback: AsyncCallback<int>): void
```

获取数据包在网络传输过程中路由器最大跳数(TTL)的值。使用callback异步回调。 > **说明：** > > 用于限制数据包在网络中传输时能够经过的最大路由器跳数的字段，TTL (Time to live)。 > > 范围为 0～255，默认值为 1 。 > > 如果一个多播数据包的 TTL 值为 1，那么它只能被直接连接到发送者的主机接收。如果 TTL 被设置为一个较大的值，那么数据包就能够被传送到更远的网络范围内。 > > 在调用 > [addMembership](#addmembership) > 之后，调用此接口才有效。

**起始版本：** 11

<!--Device-MulticastSocket-getMulticastTTL(callback: AsyncCallback<int>): void--><!--Device-MulticastSocket-getMulticastTTL(callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;int&gt; | 是 | 回调函数。失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| 2301088 | Not a socket. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';

let multicast: socket.MulticastSocket = socket.constructMulticastSocketInstance();
multicast.getMulticastTTL((err: Object, value: Number) => {
  if (err) {
    console.error('set ttl fail, err: ' + JSON.stringify(err));
    return;
  }
  console.info('set ttl success, value: ' + JSON.stringify(value));
})
```

## getMulticastTTL

```TypeScript
getMulticastTTL(): Promise<int>
```

获取数据包在网络传输过程中路由器最大跳数(TTL)的值。使用Promise异步回调。 > **说明：** > > 用于限制数据包在网络中传输时能够经过的最大路由器跳数的字段，TTL (Time to live)。 > > 范围为 0～255，默认值为 1 。 > > 如果一个多播数据包的 TTL 值为 1，那么它只能被直接连接到发送者的主机接收。如果 TTL 被设置为一个较大的值，那么数据包就能够被传送到更远的网络范围内。 > > 在调用 > [addMembership](#addmembership) > 之后，调用此接口才有效。

**起始版本：** 11

<!--Device-MulticastSocket-getMulticastTTL(): Promise<int>--><!--Device-MulticastSocket-getMulticastTTL(): Promise<int>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | 以Promise形式返回当前TTL数值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| 2301088 | Not a socket. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';

let multicast: socket.MulticastSocket = socket.constructMulticastSocketInstance();
multicast.getMulticastTTL().then((value: Number) => {
  console.info('ttl: ', JSON.stringify(value));
}).catch((err: Object) => {
  console.error('set ttl failed');
});
```

## getSocketFd

```TypeScript
getSocketFd(): Promise<int>
```

获取MulticastSocket的文件描述符。使用Promise异步回调。 > **说明：** > > - [bind](arkts-network-socket-udpsocket-i.md#bind)方法调用成功后，才可调用此方法。 > > - bind异常、Socket已关闭（如调用close后）等异常情况下调用本接口会返回-1。 > > - 文件描述符的生命周期由系统管理，应用可以通过[close](arkts-network-socket-udpsocket-i.md#close)方法关闭Socket连接，避免直接操作 > 文件描述符进行关闭。

**起始版本：** 23

**需要权限：** ohos.permission.INTERNET

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MulticastSocket-getSocketFd(): Promise<int>--><!--Device-MulticastSocket-getSocketFd(): Promise<int>-End-->

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

let multicast: socket.MulticastSocket = socket.constructMulticastSocketInstance();
let bindAddr: socket.NetAddress = {
    address: '192.168.xx.xxx',
    port: 8080
}
multicast.bind(bindAddr)
  .then(() => {
    console.info('bind success');
    multicast.getSocketFd().then((fd: number) => {
      console.info(`Socket FD：${fd}`);
    }).catch((err: BusinessError) => {
      console.error(`getSocketFd fail: ${err.message}, errorCode: ${err.code}`);
    });
  }).catch((err: BusinessError) => {
  console.error('bind fail');
});
```

## setLoopbackMode

```TypeScript
setLoopbackMode(flag: boolean, callback: AsyncCallback<void>): void
```

设置多播通信中的环回模式标志位。使用callback异步回调。 > **说明：** > > 用于设置环回模式，开启或关闭两种状态，默认为开启状态。 > > 如果一个多播通信中环回模式设置值为 true，那么它允许主机在本地循环接收自己发送的多播数据包。如果为 false，则主机不会接收到自己发送的多播数据包。 > > 在调用 > [addMembership](#addmembership) > 之后，调用此接口才有效。

**起始版本：** 11

<!--Device-MulticastSocket-setLoopbackMode(flag: boolean, callback: AsyncCallback<void>): void--><!--Device-MulticastSocket-setLoopbackMode(flag: boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| flag | boolean | 是 | 是否开启环回模式。true表示环回模式开启，false表示环回模式关闭。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| 2301088 | Not a socket. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';

let multicast: socket.MulticastSocket = socket.constructMulticastSocketInstance();
multicast.setLoopbackMode(false, (err: Object) => {
  if (err) {
    console.error('set loopback mode fail, err: ' + JSON.stringify(err));
    return;
  }
  console.info('set loopback mode success');
})
```

## setLoopbackMode

```TypeScript
setLoopbackMode(flag: boolean): Promise<void>
```

设置多播通信中的环回模式标志位。使用Promise异步回调。 > **说明：** > > 用于设置环回模式，开启或关闭两种状态，默认为开启状态。 > > 如果一个多播通信中环回模式设置值为 true，那么它允许主机在本地循环接收自己发送的多播数据包。如果为 false，则主机不会接收到自己发送的多播数据包。 > > 在调用 > [addMembership](#addmembership) > 之后，调用此接口才有效。

**起始版本：** 11

<!--Device-MulticastSocket-setLoopbackMode(flag: boolean): Promise<void>--><!--Device-MulticastSocket-setLoopbackMode(flag: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| flag | boolean | 是 | 是否开启环回模式。true表示环回模式开启，false表示环回模式关闭。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 以Promise形式返回MulticastSocket设置环回模式的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| 2301088 | Not a socket. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';

let multicast: socket.MulticastSocket = socket.constructMulticastSocketInstance();
multicast.setLoopbackMode(false).then(() => {
  console.info('set loopback mode success');
}).catch((err: Object) => {
  console.error('set loopback mode failed');
});
```

## setMulticastTTL

```TypeScript
setMulticastTTL(ttl: int, callback: AsyncCallback<void>): void
```

设置多播通信时数据包在网络传输过程中路由器最大跳数。使用callback异步回调。 > **说明：** > > 用于限制数据包在网络中传输时能够经过的最大路由器跳数的字段，TTL (Time to live)。 > > 范围为 0～255，默认值为 1 。 > > 如果一个多播数据包的 TTL 值为 1，那么它只能被直接连接到发送者的主机接收。如果 TTL 被设置为一个较大的值，那么数据包就能够被传送到更远的网络范围内。 > > 在调用 > [addMembership](#addmembership) > 之后，调用此接口才有效。

**起始版本：** 11

<!--Device-MulticastSocket-setMulticastTTL(ttl: int, callback: AsyncCallback<void>): void--><!--Device-MulticastSocket-setMulticastTTL(ttl: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ttl | int | 是 | ttl设置数值，类型为数字number。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| 2301088 | Not a socket. |
| 2301022 | Invalid argument. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';

let multicast: socket.MulticastSocket = socket.constructMulticastSocketInstance();
let ttl = 8
multicast.setMulticastTTL(ttl, (err: Object) => {
  if (err) {
    console.error('set ttl fail, err: ' + JSON.stringify(err));
    return;
  }
  console.info('set ttl success');
})
```

## setMulticastTTL

```TypeScript
setMulticastTTL(ttl: int): Promise<void>
```

设置多播通信时数据包在网络传输过程中路由器最大跳数。使用Promise异步回调。 > **说明：** > > 用于限制数据包在网络中传输时能够经过的最大路由器跳数的字段，TTL (Time to live)。 > > 范围为 0～255，默认值为 1 。 > > 如果一个多播数据包的 TTL 值为 1，那么它只能被直接连接到发送者的主机接收。如果 TTL 被设置为一个较大的值，那么数据包就能够被传送到更远的网络范围内。 > > 在调用 > [addMembership](#addmembership) > 之后，调用此接口才有效。

**起始版本：** 11

<!--Device-MulticastSocket-setMulticastTTL(ttl: int): Promise<void>--><!--Device-MulticastSocket-setMulticastTTL(ttl: int): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ttl | int | 是 | ttl设置数值，类型为数字Number。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 以Promise形式返回MulticastSocket设置TTL数值的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| 2301088 | Not a socket. |
| 2301022 | Invalid argument. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';

let multicast: socket.MulticastSocket = socket.constructMulticastSocketInstance();
multicast.setMulticastTTL(8).then(() => {
  console.info('set ttl success');
}).catch((err: Object) => {
  console.error('set ttl failed');
});
```

## setReuseAddress

```TypeScript
setReuseAddress(reuse: boolean): void
```

设置多播Socket是否支持地址复用。使用同步方式调用。 > **说明：** > > 用于控制多播Socket绑定端口时是否开启地址复用能力。 > > 如需绑定已被占用的端口，确保占用方开启了地址复用能力，同时本业务也需在调用 > [bind](arkts-network-socket-udpsocket-i.md#bind)前调用本接口以开启地址复用能力。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MulticastSocket-setReuseAddress(reuse: boolean): void--><!--Device-MulticastSocket-setReuseAddress(reuse: boolean): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reuse | boolean | 是 | 是否开启地址复用。true表示开启，false表示关闭。 |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let multicast: socket.MulticastSocket = socket.constructMulticastSocketInstance();
let bindAddr: socket.NetAddress = {
  // 0.0.0.0 表示绑定本机所有IPv4网络接口上的 8080 端口，常用于多播场景接收该端口的数据。
  address: '0.0.0.0',
  port: 8080
}

try {
  multicast.setReuseAddress(true);
  multicast.bind(bindAddr).then(() => {
    console.info('setReuseAddress success');
  }).catch((err: BusinessError) => {
    console.error(`bind failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`setReuseAddress failed, code is ${error.code}, message is ${error.message}`);
}
```

