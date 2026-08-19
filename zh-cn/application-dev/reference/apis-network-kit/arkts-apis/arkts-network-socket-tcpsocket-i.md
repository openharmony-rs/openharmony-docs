# TCPSocket

TCPSocket连接。在调用TCPSocket的方法前，需要先通过[socket.constructTCPSocketInstance](arkts-network-socket-constructtcpsocketinstance-f.md)创建 TCPSocket对象。

**起始版本：** 7

<!--Device-socket-export interface TCPSocket--><!--Device-socket-export interface TCPSocket-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## bind

```TypeScript
bind(address: NetAddress, callback: AsyncCallback<void>): void
```

绑定IP地址和端口，端口可以指定为0由系统随机分配或由用户指定为其它非0端口。使用callback异步回调。 > **说明：** > > bind方法如果因为端口冲突而执行失败，则会由系统随机分配端口号。 > > TCP客户端可先调用该接口(tcp.bind)显式绑定IP地址和端口号，再调用tcp.connect完成与服务端的连接；也可直接调用tcp.connect由系统自动绑定IP地址和端口号，完成与服务端的连接。 > > bind的IP为'localhost'或'127.0.0.1'时，只允许本地回环接口的连接，即服务端和客户端运行在同一台机器上。

**起始版本：** 7

**需要权限：** ohos.permission.INTERNET

<!--Device-TCPSocket-bind(address: NetAddress, callback: AsyncCallback<void>): void--><!--Device-TCPSocket-bind(address: NetAddress, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| address | NetAddress | 是 | 本端地址信息，参考 NetAddress。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。失败返回错误、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
let bindAddr: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
tcp.bind(bindAddr, (err: BusinessError) => {
  if (err) {
    console.error('bind fail');
    return;
  }
  console.info('bind success');
})
```

## bind

```TypeScript
bind(address: NetAddress): Promise<void>
```

绑定IP地址和端口，端口可以指定为0由系统随机分配或由用户指定为其它非0端口。使用Promise异步回调。 > **说明：** > > bind方法如果因为端口冲突而执行失败，则会由系统随机分配端口号。 > > TCP客户端可先调用该接口(tcp.bind)显式绑定IP地址和端口号，再调用tcp.connect完成与服务端的连接；也可直接调用tcp.connect由系统自动绑定IP地址和端口号，完成与服务端的连接。 > > bind的IP为'localhost'或'127.0.0.1'时，只允许本地回环接口的连接，即服务端和客户端运行在同一台机器上。

**起始版本：** 7

**需要权限：** ohos.permission.INTERNET

<!--Device-TCPSocket-bind(address: NetAddress): Promise<void>--><!--Device-TCPSocket-bind(address: NetAddress): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| address | NetAddress | 是 | 本端地址信息，参考 NetAddress。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 以Promise形式返回TCPSocket绑定本机的IP地址和端口的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
let bindAddr: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
tcp.bind(bindAddr).then(() => {
  console.info('bind success');
}).catch((err: BusinessError) => {
  console.error('bind fail');
});
```

## close

```TypeScript
close(callback: AsyncCallback<void>): void
```

关闭TCPSocket连接。使用callback异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.INTERNET

<!--Device-TCPSocket-close(callback: AsyncCallback<void>): void--><!--Device-TCPSocket-close(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();

tcp.close((err: BusinessError) => {
  if (err) {
    console.error('close fail');
    return;
  }
  console.info('close success');
})
```

## close

```TypeScript
close(): Promise<void>
```

关闭TCPSocket连接。使用Promise异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.INTERNET

<!--Device-TCPSocket-close(): Promise<void>--><!--Device-TCPSocket-close(): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();

tcp.close().then(() => {
  console.info('close success');
}).catch((err: BusinessError) => {
  console.error('close fail');
});
```

## connect

```TypeScript
connect(options: TCPConnectOptions, callback: AsyncCallback<void>): void
```

连接到指定的IP地址和端口。使用callback异步回调。 > **说明：** > > 在没有执行tcp.bind的情况下，也可以直接调用该接口完成与TCP服务端的连接

**起始版本：** 7

**需要权限：** ohos.permission.INTERNET

<!--Device-TCPSocket-connect(options: TCPConnectOptions, callback: AsyncCallback<void>): void--><!--Device-TCPSocket-connect(options: TCPConnectOptions, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TCPConnectOptions](arkts-network-socket-tcpconnectoptions-i.md) | 是 | TCPSocket连接的参数，参考[TCPConnectOptions](arkts-network-socket-tcpconnectoptions-i.md)。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2301207](../errorcode-net-socket.md#2301207-socks5认证用户名或密码无效) | Socks5 username or password is invalid.<br>**适用版本：** 18+ |
| [2301206](../errorcode-net-socket.md#2301206-socks5连接代理服务器失败) | Socks5 failed to connect to the proxy server.<br>**适用版本：** 18+ |
| [2301211](../errorcode-net-socket.md#2301211-socks5接收消息失败) | Socks5 failed to receive the message.<br>**适用版本：** 18+ |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2301210](../errorcode-net-socket.md#2301210-socks5发送消息失败) | Socks5 failed to send the message.<br>**适用版本：** 18+ |
| [2301209](../errorcode-net-socket.md#2301209-socks5协商认证方式失败) | Socks5 failed to negotiate the authentication method.<br>**适用版本：** 18+ |
| [2301208](../errorcode-net-socket.md#2301208-socks5连接远程服务器失败) | Socks5 failed to connect to the remote server.<br>**适用版本：** 18+ |
| [2301213](../errorcode-net-socket.md#2301213-socks5消息反序列化失败) | Socks5 deserialization error.<br>**适用版本：** 18+ |
| [2301212](../errorcode-net-socket.md#2301212-socks5消息序列化失败) | Socks5 serialization error.<br>**适用版本：** 18+ |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
let netAddress: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let tcpconnectoptions: socket.TCPConnectOptions = {
  address: netAddress,
  timeout: 6000
}
tcp.connect(tcpconnectoptions, (err: BusinessError) => {
  if (err) {
    console.error('connect fail');
    return;
  }
  console.info('connect success');
})
```

示例（设置socket代理）：

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
let netAddress: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let socks5Server: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let proxyOptions: socket.ProxyOptions = {
  type : 1,
  address: socks5Server,
  username: "xxx",
  password: "xxx"
}
let tcpconnectoptions: socket.TCPConnectOptions = {
  address: netAddress,
  timeout: 6000,
  proxy: proxyOptions,
}
tcp.connect(tcpconnectoptions, (err: BusinessError) => {
  if (err) {
    console.error('connect fail');
    return;
  }
  console.info('connect success');
})
```

## connect

```TypeScript
connect(options: TCPConnectOptions): Promise<void>
```

连接到指定的IP地址和端口。使用Promise异步回调。 > **说明：** > > 在没有执行tcp.bind的情况下，也可以直接调用该接口完成与TCP服务端的连接。

**起始版本：** 7

**需要权限：** ohos.permission.INTERNET

<!--Device-TCPSocket-connect(options: TCPConnectOptions): Promise<void>--><!--Device-TCPSocket-connect(options: TCPConnectOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TCPConnectOptions](arkts-network-socket-tcpconnectoptions-i.md) | 是 | TCPSocket连接的参数，参考[TCPConnectOptions](arkts-network-socket-tcpconnectoptions-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 以Promise形式返回TCPSocket连接到指定的IP地址和端口的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2301207](../errorcode-net-socket.md#2301207-socks5认证用户名或密码无效) | Socks5 username or password is invalid.<br>**适用版本：** 18+ |
| [2301206](../errorcode-net-socket.md#2301206-socks5连接代理服务器失败) | Socks5 failed to connect to the proxy server.<br>**适用版本：** 18+ |
| [2301211](../errorcode-net-socket.md#2301211-socks5接收消息失败) | Socks5 failed to receive the message.<br>**适用版本：** 18+ |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2301210](../errorcode-net-socket.md#2301210-socks5发送消息失败) | Socks5 failed to send the message.<br>**适用版本：** 18+ |
| [2301209](../errorcode-net-socket.md#2301209-socks5协商认证方式失败) | Socks5 failed to negotiate the authentication method.<br>**适用版本：** 18+ |
| [2301208](../errorcode-net-socket.md#2301208-socks5连接远程服务器失败) | Socks5 failed to connect to the remote server.<br>**适用版本：** 18+ |
| [2301213](../errorcode-net-socket.md#2301213-socks5消息反序列化失败) | Socks5 deserialization error.<br>**适用版本：** 18+ |
| [2301212](../errorcode-net-socket.md#2301212-socks5消息序列化失败) | Socks5 serialization error.<br>**适用版本：** 18+ |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
let netAddress: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let tcpconnectoptions: socket.TCPConnectOptions = {
  address: netAddress,
  timeout: 6000
}
tcp.connect(tcpconnectoptions).then(() => {
  console.info('connect success')
}).catch((err: BusinessError) => {
  console.error('connect fail');
});
```

示例（设置socket代理）：

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
let netAddress: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let socks5Server: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let proxyOptions: socket.ProxyOptions = {
  type : 1,
  address: socks5Server,
  username: "xxx",
  password: "xxx"
}
let tcpconnectoptions: socket.TCPConnectOptions = {
  address: netAddress,
  timeout: 6000,
  proxy: proxyOptions,
}
tcp.connect(tcpconnectoptions).then(() => {
  console.info('connect success')
}).catch((err: BusinessError) => {
  console.error('connect fail');
});
```

## getLocalAddress

```TypeScript
getLocalAddress(): Promise<NetAddress>
```

获取TCPSocket的本地Socket地址。使用Promise异步回调。 > **说明：** > > bind方法调用成功后，才可调用此方法。

**起始版本：** 12

<!--Device-TCPSocket-getLocalAddress(): Promise<NetAddress>--><!--Device-TCPSocket-getLocalAddress(): Promise<NetAddress>-End-->

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

let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
let bindAddr: socket.NetAddress = {
  address: '192.168.xx.xxx',
  family: 1,
  port: 8080
}
tcp.bind(bindAddr).then(() => {
  tcp.getLocalAddress().then((localAddress: socket.NetAddress) => {
    console.info("SUCCESS! Address:" + JSON.stringify(localAddress));
  }).catch((err: BusinessError) => {
    console.error("FAILED! Error:" + JSON.stringify(err));
  })
}).catch((err: BusinessError) => {
  console.error('bind fail');
});
```

## getRemoteAddress

```TypeScript
getRemoteAddress(callback: AsyncCallback<NetAddress>): void
```

获取对端Socket地址。使用callback异步回调。 > **说明：** > > connect方法调用成功后，才可调用此方法。

**起始版本：** 7

**需要权限：** ohos.permission.INTERNET

<!--Device-TCPSocket-getRemoteAddress(callback: AsyncCallback<NetAddress>): void--><!--Device-TCPSocket-getRemoteAddress(callback: AsyncCallback<NetAddress>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;NetAddress&gt; | 是 | 回调函数。成功时返回对端Socket地址，失败时返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
let netAddress: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let tcpconnectoptions: socket.TCPConnectOptions = {
  address: netAddress,
  timeout: 6000
}
tcp.connect(tcpconnectoptions, () => {
  console.info('connect success');
  tcp.getRemoteAddress((err: BusinessError, data: socket.NetAddress) => {
    if (err) {
      console.error('getRemoteAddressfail');
      return;
    }
    console.info('getRemoteAddresssuccess:' + JSON.stringify(data));
  })
});
```

## getRemoteAddress

```TypeScript
getRemoteAddress(): Promise<NetAddress>
```

获取对端Socket地址。使用Promise异步回调。 > **说明：** > > connect方法调用成功后，才可调用此方法。

**起始版本：** 7

**需要权限：** ohos.permission.INTERNET

<!--Device-TCPSocket-getRemoteAddress(): Promise<NetAddress>--><!--Device-TCPSocket-getRemoteAddress(): Promise<NetAddress>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;NetAddress&gt; | 以Promise形式返回获取对端socket地址的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
let netAddress: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let tcpconnectoptions: socket.TCPConnectOptions = {
  address: netAddress,
  timeout: 6000
}
tcp.connect(tcpconnectoptions).then(() => {
  console.info('connect success');
  tcp.getRemoteAddress().then(() => {
    console.info('getRemoteAddress success');
  }).catch((err: BusinessError) => {
    console.error('getRemoteAddressfail');
  });
}).catch((err: BusinessError) => {
  console.error('connect fail');
});
```

## getSocketFd

```TypeScript
getSocketFd(callback: AsyncCallback<int>): void
```

获取TCPSocket的文件描述符。使用callback异步回调。 > **说明：** > > - bind或connect方法调用成功后，才可调用此方法。 > > - 文件描述符的生命周期由系统管理，应用可以通过[close](arkts-network-socket-udpsocket-i.md#close)方法关闭Socket连接，避免直接操作 > 文件描述符进行关闭。

**起始版本：** 10

<!--Device-TCPSocket-getSocketFd(callback: AsyncCallback<int>): void--><!--Device-TCPSocket-getSocketFd(callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;int&gt; | 是 | 回调函数，当成功时，返回socket的文件描述符，失败时，返回undefined。 |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
let bindAddr: socket.NetAddress = {
  address: '192.168.xx.xxx',
  // 绑定指定网络接口
}
tcp.bind(bindAddr)
let netAddress: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let tcpconnectoptions: socket.TCPConnectOptions = {
  address: netAddress,
  timeout: 6000
}
tcp.connect(tcpconnectoptions)
tcp.getSocketFd((err: BusinessError, data: number) => {
  console.error("getSocketFd failed: " + err);
  console.info("socketFd: " + data);
})
```

## getSocketFd

```TypeScript
getSocketFd(): Promise<int>
```

获取TCPSocket的文件描述符。使用Promise异步回调。 > **说明：** > > - bind或connect方法调用成功后，才可调用此方法。 > > - 文件描述符的生命周期由系统管理，应用可以通过[close](arkts-network-socket-udpsocket-i.md#close)方法关闭Socket连接，避免直接操作 > 文件描述符进行关闭。

**起始版本：** 10

<!--Device-TCPSocket-getSocketFd(): Promise<int>--><!--Device-TCPSocket-getSocketFd(): Promise<int>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | 以Promise形式返回socket的文件描述符。 |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
let bindAddr: socket.NetAddress = {
    address: '192.168.xx.xxx',
  // 绑定指定网络接口
}
tcp.bind(bindAddr)
let netAddress: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let tcpconnectoptions: socket.TCPConnectOptions = {
  address: netAddress,
  timeout: 6000
}
tcp.connect(tcpconnectoptions)
tcp.getSocketFd().then((data: number) => {
  console.info("socketFd: " + data);
})
```

## getState

```TypeScript
getState(callback: AsyncCallback<SocketStateBase>): void
```

获取TCPSocket状态。使用callback异步回调。 > **说明：** > > bind或connect方法调用成功后，才可调用此方法。

**起始版本：** 7

**需要权限：** ohos.permission.INTERNET

<!--Device-TCPSocket-getState(callback: AsyncCallback<SocketStateBase>): void--><!--Device-TCPSocket-getState(callback: AsyncCallback<SocketStateBase>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[SocketStateBase](arkts-network-socket-socketstatebase-i.md)&gt; | 是 | 回调函数。成功时获取TCPSocket状态，失败时返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
let netAddress: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let tcpconnectoptions: socket.TCPConnectOptions = {
  address: netAddress,
  timeout: 6000
}
tcp.connect(tcpconnectoptions, () => {
  console.info('connect success');
  tcp.getState((err: BusinessError, data: socket.SocketStateBase) => {
    if (err) {
      console.error('getState fail');
      return;
    }
    console.info('getState success:' + JSON.stringify(data));
  });
});
```

## getState

```TypeScript
getState(): Promise<SocketStateBase>
```

获取TCPSocket状态。使用Promise异步回调。 > **说明：** > > bind或connect方法调用成功后，才可调用此方法。

**起始版本：** 7

**需要权限：** ohos.permission.INTERNET

<!--Device-TCPSocket-getState(): Promise<SocketStateBase>--><!--Device-TCPSocket-getState(): Promise<SocketStateBase>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[SocketStateBase](arkts-network-socket-socketstatebase-i.md)&gt; | 以Promise形式返回获取TCPSocket状态的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
let netAddress: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let tcpconnectoptions: socket.TCPConnectOptions = {
  address: netAddress,
  timeout: 6000
}
tcp.connect(tcpconnectoptions).then(() => {
  console.info('connect success');
  tcp.getState().then(() => {
    console.info('getState success');
  }).catch((err: BusinessError) => {
    console.error('getState fail');
  });
}).catch((err: BusinessError) => {
  console.error('connect fail');
});
```

## off('connect' | 'close')

```TypeScript
off(type: 'connect' | 'close', callback?: Callback<void>): void
```

取消订阅TCPSocket的连接事件或关闭事件。使用callback异步回调。

**起始版本：** 7

<!--Device-TCPSocket-off(type: 'connect' | 'close', callback?: Callback<void>): void--><!--Device-TCPSocket-off(type: 'connect' | 'close', callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'connect' \| 'close' | 是 | 取消订阅的事件类型。&lt;br /&gt;- 'connect'：连接事件。&lt;br /&gt;- 'close'：关闭事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | 回调函数。可以指定传入on中的callback取消对应的订阅，也可以不指定callback清空所有订阅。 |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
let callback1 = () => {
  console.info("on connect success");
}
tcp.on('connect', callback1);
// 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。
tcp.off('connect', callback1);
tcp.off('connect');
let callback2 = () => {
  console.info("on close success");
}
tcp.on('close', callback2);
// 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。
tcp.off('close', callback2);
tcp.off('close');
```

## off('connect' | 'close')

```TypeScript
off(type: 'connect' | 'close', callback?: Callback<void>): void
```

取消订阅TCPSocket的连接事件或关闭事件。使用callback异步回调。

**起始版本：** 7

<!--Device-TCPSocket-off(type: 'connect' | 'close', callback?: Callback<void>): void--><!--Device-TCPSocket-off(type: 'connect' | 'close', callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'connect' \| 'close' | 是 | 取消订阅的事件类型。&lt;br /&gt;- 'connect'：连接事件。&lt;br /&gt;- 'close'：关闭事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | 回调函数。可以指定传入on中的callback取消对应的订阅，也可以不指定callback清空所有订阅。 |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
let callback1 = () => {
  console.info("on connect success");
}
tcp.on('connect', callback1);
// 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。
tcp.off('connect', callback1);
tcp.off('connect');
let callback2 = () => {
  console.info("on close success");
}
tcp.on('close', callback2);
// 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。
tcp.off('close', callback2);
tcp.off('close');
```

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

取消订阅TCPSocket连接的error事件。使用callback异步回调。

**起始版本：** 7

<!--Device-TCPSocket-off(type: 'error', callback?: ErrorCallback): void--><!--Device-TCPSocket-off(type: 'error', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 取消订阅的事件类型。'error'：error事件。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-errorcallback-t.md) | 否 | 回调函数。可以指定传入on中的callback取消对应的订阅，也可以不指定callback清空所有订阅。 |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
let callback = (err: BusinessError) => {
  console.error("on error, err:" + JSON.stringify(err));
}
tcp.on('error', callback);
// 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。
tcp.off('error', callback);
tcp.off('error');
```

## off('message')

```TypeScript
off(type: 'message', callback?: Callback<SocketMessageInfo>): void
```

取消订阅TCPSocket连接的接收消息事件。使用callback异步回调。

**起始版本：** 7

<!--Device-TCPSocket-off(type: 'message', callback?: Callback<SocketMessageInfo>): void--><!--Device-TCPSocket-off(type: 'message', callback?: Callback<SocketMessageInfo>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'message' | 是 | 取消订阅的事件类型。'message'：接收消息事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[SocketMessageInfo](arkts-network-socket-socketmessageinfo-i.md)&gt; | 否 | 回调函数。可以指定传入on中的callback取消对应的订阅，也可以不指定callback清空所有订阅。<br>**起始版本：** 11 |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
let messageView = '';
let callback = (value: socket.SocketMessageInfo) => {
  for (let i: number = 0; i < value.message.byteLength; i++) {
    let uint8Array = new Uint8Array(value.message) 
    let messages = uint8Array[i]
    let message = String.fromCharCode(messages);
    messageView += message;
  }
  console.info('on message message: ' + JSON.stringify(messageView));
  console.info('remoteInfo: ' + JSON.stringify(value.remoteInfo));
}
tcp.on('message', callback);
// 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。
tcp.off('message', callback);
tcp.off('message');
```

## on('connect' | 'close')

```TypeScript
on(type: 'connect' | 'close', callback: Callback<void>): void
```

订阅TCPSocket的连接事件或关闭事件。使用callback异步回调。

**起始版本：** 7

<!--Device-TCPSocket-on(type: 'connect' | 'close', callback: Callback<void>): void--><!--Device-TCPSocket-on(type: 'connect' | 'close', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'connect' \| 'close' | 是 | 订阅的事件类型。&lt;br /&gt;- 'connect'：连接事件。&lt;br /&gt;- 'close'：关闭事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | 回调函数。TCPSocket的连接事件或关闭事件触发时调用回调函数。 |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
tcp.on('connect', () => {
  console.info("on connect success")
});
tcp.on('close', () => {
  console.info("on close success")
});
```

## on('connect' | 'close')

```TypeScript
on(type: 'connect' | 'close', callback: Callback<void>): void
```

订阅TCPSocket的连接事件或关闭事件。使用callback异步回调。

**起始版本：** 7

<!--Device-TCPSocket-on(type: 'connect' | 'close', callback: Callback<void>): void--><!--Device-TCPSocket-on(type: 'connect' | 'close', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'connect' \| 'close' | 是 | 订阅的事件类型。&lt;br /&gt;- 'connect'：连接事件。&lt;br /&gt;- 'close'：关闭事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | 回调函数。TCPSocket的连接事件或关闭事件触发时调用回调函数。 |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
tcp.on('connect', () => {
  console.info("on connect success")
});
tcp.on('close', () => {
  console.info("on close success")
});
```

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

订阅TCPSocket连接的error事件。使用callback异步回调。

**起始版本：** 7

<!--Device-TCPSocket-on(type: 'error', callback: ErrorCallback): void--><!--Device-TCPSocket-on(type: 'error', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 订阅的事件类型。'error'：error事件。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-errorcallback-t.md) | 是 | 回调函数。TCPSocket连接订阅的某类error事件触发时调用回调函数。 |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
tcp.on('error', (err: BusinessError) => {
  console.error("on error, err:" + JSON.stringify(err))
});
```

## on('message')

```TypeScript
on(type: 'message', callback: Callback<SocketMessageInfo>): void
```

订阅TCPSocket连接的接收消息事件。使用callback异步回调。

**起始版本：** 7

<!--Device-TCPSocket-on(type: 'message', callback: Callback<SocketMessageInfo>): void--><!--Device-TCPSocket-on(type: 'message', callback: Callback<SocketMessageInfo>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'message' | 是 | 订阅的事件类型。'message'：接收消息事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[SocketMessageInfo](arkts-network-socket-socketmessageinfo-i.md)&gt; | 是 | 回调函数。返回TCPSocket连接信息。<br>**起始版本：** 11 |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
tcp.on('message', (value: socket.SocketMessageInfo) => {
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
```

## send

```TypeScript
send(options: TCPSendOptions, callback: AsyncCallback<void>): void
```

通过TCPSocket连接发送数据。使用callback异步回调。 > **说明：** > > connect方法调用成功后，才可调用此方法。该接口为耗时操作，请在Worker线程或taskpool线程调用该接口。

**起始版本：** 7

**需要权限：** ohos.permission.INTERNET

<!--Device-TCPSocket-send(options: TCPSendOptions, callback: AsyncCallback<void>): void--><!--Device-TCPSocket-send(options: TCPSendOptions, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TCPSendOptions](arkts-network-socket-tcpsendoptions-i.md) | 是 | TCPSocket发送请求的参数，参考[TCPSendOptions](arkts-network-socket-tcpsendoptions-i.md)。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
let netAddress: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let tcpconnectoptions: socket.TCPConnectOptions = {
  address: netAddress,
  timeout: 6000
}
tcp.connect(tcpconnectoptions, () => {
  console.info('connect success');
  let tcpSendOptions: socket.TCPSendOptions = {
    data: 'Hello, server!'
  }
  tcp.send(tcpSendOptions, (err: BusinessError) => {
    if (err) {
      console.error('send fail');
      return;
    }
    console.info('send success');
  })
})
```

## send

```TypeScript
send(options: TCPSendOptions): Promise<void>
```

通过TCPSocket连接发送数据。使用Promise异步回调。 > **说明：** > > connect方法调用成功后，才可调用此方法。该接口为耗时操作，请在Worker线程或taskpool线程调用该接口。

**起始版本：** 7

**需要权限：** ohos.permission.INTERNET

<!--Device-TCPSocket-send(options: TCPSendOptions): Promise<void>--><!--Device-TCPSocket-send(options: TCPSendOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TCPSendOptions](arkts-network-socket-tcpsendoptions-i.md) | 是 | TCPSocket发送请求的参数，参考[TCPSendOptions](arkts-network-socket-tcpsendoptions-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
let netAddress: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let tcpconnectoptions: socket.TCPConnectOptions = {
  address: netAddress,
  timeout: 6000
}
tcp.connect(tcpconnectoptions, () => {
  console.info('connect success');
  let tcpSendOptions: socket.TCPSendOptions = {
    data: 'Hello, server!'
  }
  tcp.send(tcpSendOptions).then(() => {
    console.info('send success');
  }).catch((err: BusinessError) => {
    console.error('send fail');
  });
})
```

## setExtraOptions

```TypeScript
setExtraOptions(options: TCPExtraOptions, callback: AsyncCallback<void>): void
```

设置TCPSocket连接的其他属性。使用callback异步回调。 > **说明：** > > bind或connect方法调用成功后，才可调用此方法。

**起始版本：** 7

**需要权限：** ohos.permission.INTERNET

<!--Device-TCPSocket-setExtraOptions(options: TCPExtraOptions, callback: AsyncCallback<void>): void--><!--Device-TCPSocket-setExtraOptions(options: TCPExtraOptions, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TCPExtraOptions](arkts-network-socket-tcpextraoptions-i.md) | 是 | TCPSocket连接的其他属性，参考[TCPExtraOptions](arkts-network-socket-tcpextraoptions-i.md)。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。失败时返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
let netAddress: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let tcpconnectoptions: socket.TCPConnectOptions = {
  address: netAddress,
  timeout: 6000
}

interface SocketLinger {
  on: boolean;
  linger: number;
}

tcp.connect(tcpconnectoptions, () => {
  console.info('connect success');
  let tcpExtraOptions: socket.TCPExtraOptions = {
    keepAlive: true,
    OOBInline: true,
    TCPNoDelay: true,
    socketLinger: { on: true, linger: 10 } as SocketLinger,
    receiveBufferSize: 8192,
    sendBufferSize: 8192,
    reuseAddress: true,
    socketTimeout: 3000,
    tcpFastOpen: false
  }
  tcp.setExtraOptions(tcpExtraOptions, (err: BusinessError) => {
    if (err) {
      console.error('setExtraOptions fail');
      return;
    }
    console.info('setExtraOptions success');
  });
});
```

## setExtraOptions

```TypeScript
setExtraOptions(options: TCPExtraOptions): Promise<void>
```

设置TCPSocket连接的其他属性。使用Promise异步回调。 > **说明：** > > bind或connect方法调用成功后，才可调用此方法。

**起始版本：** 7

**需要权限：** ohos.permission.INTERNET

<!--Device-TCPSocket-setExtraOptions(options: TCPExtraOptions): Promise<void>--><!--Device-TCPSocket-setExtraOptions(options: TCPExtraOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TCPExtraOptions](arkts-network-socket-tcpextraoptions-i.md) | 是 | TCPSocket连接的其他属性，参考[TCPExtraOptions](arkts-network-socket-tcpextraoptions-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
let netAddress: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let tcpconnectoptions: socket.TCPConnectOptions = {
  address: netAddress,
  timeout: 6000
}

interface SocketLinger {
  on: boolean;
  linger: number;
}

tcp.connect(tcpconnectoptions, () => {
  console.info('connect success');
  let tcpExtraOptions: socket.TCPExtraOptions = {
    keepAlive: true,
    OOBInline: true,
    TCPNoDelay: true,
    socketLinger: { on: true, linger: 10 } as SocketLinger,
    receiveBufferSize: 8192,
    sendBufferSize: 8192,
    reuseAddress: true,
    socketTimeout: 3000,
    tcpFastOpen: false
  }
  tcp.setExtraOptions(tcpExtraOptions).then(() => {
    console.info('setExtraOptions success');
  }).catch((err: BusinessError) => {
    console.error('setExtraOptions fail');
  });
});
```

