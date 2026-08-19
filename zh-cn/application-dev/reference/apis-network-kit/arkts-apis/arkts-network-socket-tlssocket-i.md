# TLSSocket

TLSSocket连接。在调用TLSSocket的方法前，需要先通过[socket.constructTLSSocketInstance](arkts-network-socket-constructtlssocketinstance-f.md)创建 TLSSocket对象。

**起始版本：** 9

<!--Device-socket-export interface TLSSocket--><!--Device-socket-export interface TLSSocket-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## bind

```TypeScript
bind(address: NetAddress, callback: AsyncCallback<void>): void
```

绑定IP地址和端口。使用callback异步回调。 > **说明：** > > 如果TLSSocket对象是通过TCPSocket对象升级创建的，可以不用执行bind方法。

**起始版本：** 9

**需要权限：** ohos.permission.INTERNET

<!--Device-TLSSocket-bind(address: NetAddress, callback: AsyncCallback<void>): void--><!--Device-TLSSocket-bind(address: NetAddress, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| address | NetAddress | 是 | 本端地址信息，参考 NetAddress。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。成功返回TLSSocket绑定本机的IP地址和端口的结果。失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2303198](../errorcode-net-socket.md#2303198-网络地址已被使用) | Address already in use. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
let bindAddr: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
tls.bind(bindAddr, (err: BusinessError) => {
  if (err) {
    console.error('bind fail');
    return;
  }
  console.info('bind success');
});
```

## bind

```TypeScript
bind(address: NetAddress): Promise<void>
```

绑定IP地址和端口。使用Promise异步回调。 > **说明：** > > 如果TLSSocket对象是通过TCPSocket对象升级创建的，可以不用执行bind方法。

**起始版本：** 9

**需要权限：** ohos.permission.INTERNET

<!--Device-TLSSocket-bind(address: NetAddress): Promise<void>--><!--Device-TLSSocket-bind(address: NetAddress): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| address | NetAddress | 是 | 本端地址信息，参考 NetAddress。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 以Promise形式返回TLSSocket绑定本机的IP地址和端口的结果。失败返回错误码，错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2303198](../errorcode-net-socket.md#2303198-网络地址已被使用) | Address already in use. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
let bindAddr: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
tls.bind(bindAddr).then(() => {
  console.info('bind success');
}).catch((err: BusinessError) => {
  console.error('bind fail');
});
```

## close

```TypeScript
close(callback: AsyncCallback<void>): void
```

在TLSSocket通信连接成功之后，断开连接，使用callback异步回调。

**起始版本：** 9

<!--Device-TLSSocket-close(callback: AsyncCallback<void>): void--><!--Device-TLSSocket-close(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数,成功返回TLSSocket关闭连接的结果。失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2303506](../errorcode-net-socket.md#2303506-关闭tls连接失败) | Failed to close the TLS connection. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2303505](../errorcode-net-socket.md#2303505-tls系统调用错误) | An error occurred in the TLS system call. |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
tls.close((err: BusinessError) => {
  if (err) {
    console.error("close callback error = " + err);
  } else {
    console.info("close success");
  }
});
```

## close

```TypeScript
close(): Promise<void>
```

在TLSSocket通信连接成功之后，断开连接，使用Promise异步回调。

**起始版本：** 9

<!--Device-TLSSocket-close(): Promise<void>--><!--Device-TLSSocket-close(): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 以Promise形式返回,返回TLSSocket关闭连接的结果。失败返回错误码，错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2303506](../errorcode-net-socket.md#2303506-关闭tls连接失败) | Failed to close the TLS connection. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2303505](../errorcode-net-socket.md#2303505-tls系统调用错误) | An error occurred in the TLS system call. |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
tls.close().then(() => {
  console.info("close success");
}).catch((err: BusinessError) => {
  console.error("failed" + err);
});
```

## connect

```TypeScript
connect(options: TLSConnectOptions, callback: AsyncCallback<void>): void
```

在TLSSocket上bind成功之后，进行通信连接，并创建和初始化TLS会话，实现建立连接过程，启动与服务器的TLS/SSL握手，实现数据传输功能，使用callback异步回调。需要注意options入参下 secureOptions内的ca在API11及之前的版本为必填项，需填入服务端的ca证书(用于认证校验服务端的数字证书)，证书内容以"-----BEGIN CERTIFICATE-----"开头，以"-----END CERTIFICATE-----"结尾，自API12开始，为非必填项。

**起始版本：** 9

<!--Device-TLSSocket-connect(options: TLSConnectOptions, callback: AsyncCallback<void>): void--><!--Device-TLSSocket-connect(options: TLSConnectOptions, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TLSConnectOptions](arkts-network-socket-tlsconnectoptions-i.md) | 是 | TLSSocket连接所需要的参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数，成功无返回，失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2303104](../errorcode-net-socket.md#2303104-中断系统调用) | Interrupted system call. |
| [2303111](../errorcode-net-socket.md#2303111-资源暂时不可用请重试) | Resource temporarily unavailable. Try again. |
| [2303109](../errorcode-net-socket.md#2303109-错误文件编号) | Bad file number. |
| [2303210](../errorcode-net-socket.md#2303210-连接超时) | Connection timed out. |
| [2303503](../errorcode-net-socket.md#2303503-tls写入错误) | An error occurred when writing data on the TLS socket. |
| [2303502](../errorcode-net-socket.md#2303502-tls读取错误) | An error occurred when reading data on the TLS socket. |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2303506](../errorcode-net-socket.md#2303506-关闭tls连接失败) | Failed to close the TLS connection. |
| [2303505](../errorcode-net-socket.md#2303505-tls系统调用错误) | An error occurred in the TLS system call. |
| [2303191](../errorcode-net-socket.md#2303191-socket协议类型错误) | Incorrect socket protocol type. |
| [2301207](../errorcode-net-socket.md#2301207-socks5认证用户名或密码无效) | Socks5 username or password is invalid.<br>**适用版本：** 18+ |
| [2301206](../errorcode-net-socket.md#2301206-socks5连接代理服务器失败) | Socks5 failed to connect to the proxy server.<br>**适用版本：** 18+ |
| [2303188](../errorcode-net-socket.md#2303188-非套接字的套接字操作) | Socket operation on non-socket. |
| [2301211](../errorcode-net-socket.md#2301211-socks5接收消息失败) | Socks5 failed to receive the message.<br>**适用版本：** 18+ |
| [2301210](../errorcode-net-socket.md#2301210-socks5发送消息失败) | Socks5 failed to send the message.<br>**适用版本：** 18+ |
| [2301209](../errorcode-net-socket.md#2301209-socks5协商认证方式失败) | Socks5 failed to negotiate the authentication method.<br>**适用版本：** 18+ |
| [2301208](../errorcode-net-socket.md#2301208-socks5连接远程服务器失败) | Socks5 failed to connect to the remote server.<br>**适用版本：** 18+ |
| [2303199](../errorcode-net-socket.md#2303199-不能分配请求的地址) | Cannot assign requested address. |
| [2303198](../errorcode-net-socket.md#2303198-网络地址已被使用) | Address already in use. |
| [2301213](../errorcode-net-socket.md#2301213-socks5消息反序列化失败) | Socks5 deserialization error.<br>**适用版本：** 18+ |
| [2301212](../errorcode-net-socket.md#2301212-socks5消息序列化失败) | Socks5 serialization error.<br>**适用版本：** 18+ |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tlsTwoWay: socket.TLSSocket = socket.constructTLSSocketInstance();  // Two way authentication
let bindAddr: socket.NetAddress = {
    address: '192.168.xx.xxx',
  // 绑定指定网络接口
}
tlsTwoWay.bind(bindAddr, (err: BusinessError) => {
  if (err) {
    console.error('bind fail');
    return;
  }
  console.info('bind success');
});
let twoWayNetAddr: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let twoWaySecureOptions: socket.TLSSecureOptions = {
  key: "xxxx",
  cert: ["xxxx"],
  ca: ["xxxx"],
  password: "xxxx",
  protocols: socket.Protocol.TLSv12,
  useRemoteCipherPrefer: true,
  signatureAlgorithms: "rsa_pss_rsae_sha256:ECDSA+SHA256",
  cipherSuite: "AES256-SHA256"
}
let tlsConnectOptions: socket.TLSConnectOptions = {
  address: twoWayNetAddr,
  secureOptions: twoWaySecureOptions,
  ALPNProtocols: ["spdy/1", "http/1.1"]
}

tlsTwoWay.connect(tlsConnectOptions, (err: BusinessError) => {
  console.error("connect callback error" + err);
});

let tlsOneWay: socket.TLSSocket = socket.constructTLSSocketInstance(); // One way authentication
tlsOneWay.bind(bindAddr, (err: BusinessError) => {
  if (err) {
    console.error('bind fail');
    return;
  }
  console.info('bind success');
});
let oneWayNetAddr: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let oneWaySecureOptions: socket.TLSSecureOptions = {
  ca: ["xxxx", "xxxx"],
  cipherSuite: "AES256-SHA256"
}
let tlsOneWayConnectOptions: socket.TLSConnectOptions = {
  address: oneWayNetAddr,
  secureOptions: oneWaySecureOptions
}
tlsOneWay.connect(tlsOneWayConnectOptions, (err: BusinessError) => {
  console.error("connect callback error" + err);
});
```

示例（设置socket代理）：

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tlsTwoWay: socket.TLSSocket = socket.constructTLSSocketInstance();  // 双向认证
let bindAddr: socket.NetAddress = {
   address: '192.168.xx.xxx',
  // 绑定指定网络接口
}
tlsTwoWay.bind(bindAddr, (err: BusinessError) => {
  if (err) {
    console.error('bind fail');
    return;
  }
  console.info('bind success');
});
let twoWayNetAddr: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let socks5Server: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let twoWaySecureOptions: socket.TLSSecureOptions = {
  key: "xxxx",
  cert: ["xxxx"],
  ca: ["xxxx"],
  password: "xxxx",
  protocols: socket.Protocol.TLSv12,
  useRemoteCipherPrefer: true,
  signatureAlgorithms: "rsa_pss_rsae_sha256:ECDSA+SHA256",
  cipherSuite: "AES256-SHA256"
}
let proxyOptions: socket.ProxyOptions = {
  type : 1,
  address: socks5Server,
  username: "xxx",
  password: "xxx"
}
let tlsConnectOptions: socket.TLSConnectOptions = {
  address: twoWayNetAddr,
  secureOptions: twoWaySecureOptions,
  ALPNProtocols: ["spdy/1", "http/1.1"],
  proxy: proxyOptions,
}

tlsTwoWay.connect(tlsConnectOptions, (err: BusinessError) => {
  console.error("connect callback error" + err);
});

let tlsOneWay: socket.TLSSocket = socket.constructTLSSocketInstance(); // 单向认证
tlsOneWay.bind(bindAddr, (err: BusinessError) => {
  if (err) {
    console.error('bind fail');
    return;
  }
  console.info('bind success');
});
let oneWayNetAddr: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let oneWaySecureOptions: socket.TLSSecureOptions = {
  ca: ["xxxx", "xxxx"],
  cipherSuite: "AES256-SHA256"
}
let oneWayProxyOptions: socket.ProxyOptions = {
  type : 1,
  address: socks5Server,
  username: "xxx",
  password: "xxx"
}
let tlsOneWayConnectOptions: socket.TLSConnectOptions = {
  address: oneWayNetAddr,
  secureOptions: oneWaySecureOptions,
  proxy: oneWayProxyOptions,
}
tlsOneWay.connect(tlsOneWayConnectOptions, (err: BusinessError) => {
  console.error("connect callback error" + err);
});
```

## connect

```TypeScript
connect(options: TLSConnectOptions): Promise<void>
```

在TLSSocket上bind成功之后，进行通信连接，并创建和初始化TLS会话，实现建立连接过程，启动与服务器的TLS/SSL握手，实现数据传输功能，该连接包括两种认证方式，单向认证与双向认证，使用Promise异步回调。需要 注意options入参下secureOptions内的ca在API11及之前的版本为必填项，需填入服务端的ca证书(用于认证校验服务端的数字证书)，证书内容以"-----BEGIN CERTIFICATE-----"开头，以" -----END CERTIFICATE-----"结尾，自API12开始，为非必填项。

**起始版本：** 9

<!--Device-TLSSocket-connect(options: TLSConnectOptions): Promise<void>--><!--Device-TLSSocket-connect(options: TLSConnectOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TLSConnectOptions](arkts-network-socket-tlsconnectoptions-i.md) | 是 | 连接所需要的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 以Promise形式返回，成功无返回，失败返回错误码，错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2303104](../errorcode-net-socket.md#2303104-中断系统调用) | Interrupted system call. |
| [2303111](../errorcode-net-socket.md#2303111-资源暂时不可用请重试) | Resource temporarily unavailable. Try again. |
| [2303109](../errorcode-net-socket.md#2303109-错误文件编号) | Bad file number. |
| [2303210](../errorcode-net-socket.md#2303210-连接超时) | Connection timed out. |
| [2303503](../errorcode-net-socket.md#2303503-tls写入错误) | An error occurred when writing data on the TLS socket. |
| [2303502](../errorcode-net-socket.md#2303502-tls读取错误) | An error occurred when reading data on the TLS socket. |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2303506](../errorcode-net-socket.md#2303506-关闭tls连接失败) | Failed to close the TLS connection. |
| [2303505](../errorcode-net-socket.md#2303505-tls系统调用错误) | An error occurred in the TLS system call. |
| [2303191](../errorcode-net-socket.md#2303191-socket协议类型错误) | Incorrect socket protocol type. |
| [2301207](../errorcode-net-socket.md#2301207-socks5认证用户名或密码无效) | Socks5 username or password is invalid.<br>**适用版本：** 18+ |
| [2301206](../errorcode-net-socket.md#2301206-socks5连接代理服务器失败) | Socks5 failed to connect to the proxy server.<br>**适用版本：** 18+ |
| [2303188](../errorcode-net-socket.md#2303188-非套接字的套接字操作) | Socket operation on non-socket. |
| [2301211](../errorcode-net-socket.md#2301211-socks5接收消息失败) | Socks5 failed to receive the message.<br>**适用版本：** 18+ |
| [2301210](../errorcode-net-socket.md#2301210-socks5发送消息失败) | Socks5 failed to send the message.<br>**适用版本：** 18+ |
| [2301209](../errorcode-net-socket.md#2301209-socks5协商认证方式失败) | Socks5 failed to negotiate the authentication method.<br>**适用版本：** 18+ |
| [2301208](../errorcode-net-socket.md#2301208-socks5连接远程服务器失败) | Socks5 failed to connect to the remote server.<br>**适用版本：** 18+ |
| [2303199](../errorcode-net-socket.md#2303199-不能分配请求的地址) | Cannot assign requested address. |
| [2303198](../errorcode-net-socket.md#2303198-网络地址已被使用) | Address already in use. |
| [2301213](../errorcode-net-socket.md#2301213-socks5消息反序列化失败) | Socks5 deserialization error.<br>**适用版本：** 18+ |
| [2301212](../errorcode-net-socket.md#2301212-socks5消息序列化失败) | Socks5 serialization error.<br>**适用版本：** 18+ |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tlsTwoWay: socket.TLSSocket = socket.constructTLSSocketInstance();  // Two way authentication
let bindAddr: socket.NetAddress = {
   address: '192.168.xx.xxx',
  // 绑定指定网络接口
}
tlsTwoWay.bind(bindAddr, (err: BusinessError) => {
  if (err) {
    console.error('bind fail');
    return;
  }
  console.info('bind success');
});
let twoWayNetAddr: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let twoWaySecureOptions: socket.TLSSecureOptions = {
  key: "xxxx",
  cert: ["xxxx"],
  ca: ["xxxx"],
  password: "xxxx",
  protocols: socket.Protocol.TLSv12,
  useRemoteCipherPrefer: true,
  signatureAlgorithms: "rsa_pss_rsae_sha256:ECDSA+SHA256",
  cipherSuite: "AES256-SHA256"
}
let tlsConnectOptions: socket.TLSConnectOptions = {
  address: twoWayNetAddr,
  secureOptions: twoWaySecureOptions,
  ALPNProtocols: ["spdy/1", "http/1.1"]
}

tlsTwoWay.connect(tlsConnectOptions).then(() => {
  console.info("connect successfully");
}).catch((err: BusinessError) => {
  console.error("connect failed " + JSON.stringify(err));
});

let tlsOneWay: socket.TLSSocket = socket.constructTLSSocketInstance(); // One way authentication
tlsOneWay.bind(bindAddr, (err: BusinessError) => {
  if (err) {
    console.error('bind fail');
    return;
  }
  console.info('bind success');
});
let oneWayNetAddr: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let oneWaySecureOptions: socket.TLSSecureOptions = {
  ca: ["xxxx", "xxxx"],
  cipherSuite: "AES256-SHA256"
}
let tlsOneWayConnectOptions: socket.TLSConnectOptions = {
  address: oneWayNetAddr,
  secureOptions: oneWaySecureOptions
}
tlsOneWay.connect(tlsOneWayConnectOptions).then(() => {
  console.info("connect successfully");
}).catch((err: BusinessError) => {
  console.error("connect failed " + JSON.stringify(err));
});
```

示例（设置socket代理）：

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tlsTwoWay: socket.TLSSocket = socket.constructTLSSocketInstance();  // 双向认证
let bindAddr: socket.NetAddress = {
   address: '192.168.xx.xxx',
  // 绑定指定网络接口
}
tlsTwoWay.bind(bindAddr, (err: BusinessError) => {
  if (err) {
    console.error('bind fail');
    return;
  }
  console.info('bind success');
});
let twoWayNetAddr: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let socks5Server: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let twoWaySecureOptions: socket.TLSSecureOptions = {
  key: "xxxx",
  cert: ["xxxx"],
  ca: ["xxxx"],
  password: "xxxx",
  protocols: socket.Protocol.TLSv12,
  useRemoteCipherPrefer: true,
  signatureAlgorithms: "rsa_pss_rsae_sha256:ECDSA+SHA256",
  cipherSuite: "AES256-SHA256"
}
let proxyOptions: socket.ProxyOptions = {
  type : 1,
  address: socks5Server,
  username: "xxx",
  password: "xxx"
}
let tlsConnectOptions: socket.TLSConnectOptions = {
  address: twoWayNetAddr,
  secureOptions: twoWaySecureOptions,
  ALPNProtocols: ["spdy/1", "http/1.1"],
  proxy: proxyOptions,
}

tlsTwoWay.connect(tlsConnectOptions).then(() => {
  console.info("connect successfully");
}).catch((err: BusinessError) => {
  console.error("connect failed " + JSON.stringify(err));
});

let tlsOneWay: socket.TLSSocket = socket.constructTLSSocketInstance(); // 单向认证
tlsOneWay.bind(bindAddr, (err: BusinessError) => {
  if (err) {
    console.error('bind fail');
    return;
  }
  console.info('bind success');
});
let oneWayNetAddr: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let oneWaySecureOptions: socket.TLSSecureOptions = {
  ca: ["xxxx", "xxxx"],
  cipherSuite: "AES256-SHA256"
}
let oneWayProxyOptions: socket.ProxyOptions = {
  type : 1,
  address: socks5Server,
  username: "xxx",
  password: "xxx"
}
let tlsOneWayConnectOptions: socket.TLSConnectOptions = {
  address: oneWayNetAddr,
  secureOptions: oneWaySecureOptions,
  proxy: oneWayProxyOptions,
}
tlsOneWay.connect(tlsOneWayConnectOptions).then(() => {
  console.info("connect successfully");
}).catch((err: BusinessError) => {
  console.error("connect failed " + JSON.stringify(err));
});
```

## getCertificate

```TypeScript
getCertificate(callback: AsyncCallback<X509CertRawData>): void
```

在TLSSocket通信连接成功之后，获取本地的数字证书，该接口只适用于双向认证时，使用callback异步回调。

**起始版本：** 9

<!--Device-TLSSocket-getCertificate(callback: AsyncCallback<X509CertRawData>): void--><!--Device-TLSSocket-getCertificate(callback: AsyncCallback<X509CertRawData>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[X509CertRawData](arkts-network-socket-x509certrawdata-t.md)&gt; | 是 | 回调函数，成功返回本地的证书，失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2303504](../errorcode-net-socket.md#2303504-查找x509时出错) | An error occurred when verifying the X.509 certificate. |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |

## getCertificate

```TypeScript
getCertificate(): Promise<X509CertRawData>
```

在TLSSocket通信连接之后，获取本地的数字证书，该接口只适用于双向认证时，使用Promise异步回调。

**起始版本：** 9

<!--Device-TLSSocket-getCertificate(): Promise<X509CertRawData>--><!--Device-TLSSocket-getCertificate(): Promise<X509CertRawData>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[X509CertRawData](arkts-network-socket-x509certrawdata-t.md)&gt; | 以Promise形式返回本地的数字证书的结果。失败返回错误码，错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2303504](../errorcode-net-socket.md#2303504-查找x509时出错) | An error occurred when verifying the X.509 certificate. |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |

## getCipherSuite

```TypeScript
getCipherSuite(callback: AsyncCallback<Array<string>>): void
```

在TLSSocket通信连接成功之后，获取通信双方协商后的加密套件，使用callback异步回调。

**起始版本：** 9

<!--Device-TLSSocket-getCipherSuite(callback: AsyncCallback<Array<string>>): void--><!--Device-TLSSocket-getCipherSuite(callback: AsyncCallback<Array<string>>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;string&gt;&gt; | 是 | 回调函数，返回通信双方支持的加密套件。失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2303505](../errorcode-net-socket.md#2303505-tls系统调用错误) | An error occurred in the TLS system call. |
| [2303502](../errorcode-net-socket.md#2303502-tls读取错误) | An error occurred when reading data on the TLS socket. |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
tls.getCipherSuite((err: BusinessError, data: Array<string>) => {
  if (err) {
    console.error("getCipherSuite callback error = " + err);
  } else {
    console.info("getCipherSuite callback = " + data);
  }
});
```

## getCipherSuite

```TypeScript
getCipherSuite(): Promise<Array<string>>
```

在TLSSocket通信连接成功之后，获取通信双方协商后的加密套件，使用Promise异步回调。

**起始版本：** 9

<!--Device-TLSSocket-getCipherSuite(): Promise<Array<string>>--><!--Device-TLSSocket-getCipherSuite(): Promise<Array<string>>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | 以Promise形式返回通信双方支持的加密套件。失败返回错误码，错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2303505](../errorcode-net-socket.md#2303505-tls系统调用错误) | An error occurred in the TLS system call. |
| [2303502](../errorcode-net-socket.md#2303502-tls读取错误) | An error occurred when reading data on the TLS socket. |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
tls.getCipherSuite().then((data: Array<string>) => {
  console.info('getCipherSuite success:' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error("failed" + err);
});
```

## getLocalAddress

```TypeScript
getLocalAddress(): Promise<NetAddress>
```

获取TLSSocket的本地Socket地址。使用Promise异步回调。 > **说明：** > > 在TLSSocketServer通信连接成功之后，才可调用此方法。

**起始版本：** 12

<!--Device-TLSSocket-getLocalAddress(): Promise<NetAddress>--><!--Device-TLSSocket-getLocalAddress(): Promise<NetAddress>-End-->

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

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
tls.getLocalAddress().then((localAddress: socket.NetAddress) => {
  console.info("Get success: " + JSON.stringify(localAddress));
}).catch((err: BusinessError) => {
  console.error("Get failed, error: " + JSON.stringify(err));
})
```

## getProtocol

```TypeScript
getProtocol(callback: AsyncCallback<string>): void
```

在TLSSocket通信连接成功之后，获取通信的协议版本，使用callback异步回调。

**起始版本：** 9

<!--Device-TLSSocket-getProtocol(callback: AsyncCallback<string>): void--><!--Device-TLSSocket-getProtocol(callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;string&gt; | 是 | 回调函数，返回通信的协议。失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2303505](../errorcode-net-socket.md#2303505-tls系统调用错误) | An error occurred in the TLS system call. |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
tls.getProtocol((err: BusinessError, data: string) => {
  if (err) {
    console.error("getProtocol callback error = " + err);
  } else {
    console.info("getProtocol callback = " + data);
  }
});
```

## getProtocol

```TypeScript
getProtocol(): Promise<string>
```

在TLSSocket通信连接成功之后，获取通信的协议版本，使用Promise异步回调。

**起始版本：** 9

<!--Device-TLSSocket-getProtocol(): Promise<string>--><!--Device-TLSSocket-getProtocol(): Promise<string>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | 以Promise形式返回通信的协议。失败返回错误码，错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2303505](../errorcode-net-socket.md#2303505-tls系统调用错误) | An error occurred in the TLS system call. |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
tls.getProtocol().then((data: string) => {
  console.info(data);
}).catch((err: BusinessError) => {
  console.error("failed" + err);
});
```

## getRemoteAddress

```TypeScript
getRemoteAddress(callback: AsyncCallback<NetAddress>): void
```

在TLSSocket通信连接成功之后，获取对端Socket地址。使用callback异步回调。

**起始版本：** 9

<!--Device-TLSSocket-getRemoteAddress(callback: AsyncCallback<NetAddress>): void--><!--Device-TLSSocket-getRemoteAddress(callback: AsyncCallback<NetAddress>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;NetAddress&gt; | 是 | 回调函数。成功返回对端的socket地址，失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2303188](../errorcode-net-socket.md#2303188-非套接字的套接字操作) | Socket operation on non-socket. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
tls.getRemoteAddress((err: BusinessError, data: socket.NetAddress) => {
  if (err) {
    console.error('getRemoteAddress fail');
    return;
  }
  console.info('getRemoteAddress success:' + JSON.stringify(data));
});
```

## getRemoteAddress

```TypeScript
getRemoteAddress(): Promise<NetAddress>
```

在TLSSocket通信连接成功之后，获取对端Socket地址。使用Promise异步回调。

**起始版本：** 9

<!--Device-TLSSocket-getRemoteAddress(): Promise<NetAddress>--><!--Device-TLSSocket-getRemoteAddress(): Promise<NetAddress>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;NetAddress&gt; | 以Promise形式返回获取对端socket地址的结果。失败返回错误码，错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2303188](../errorcode-net-socket.md#2303188-非套接字的套接字操作) | Socket operation on non-socket. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
tls.getRemoteAddress().then(() => {
  console.info('getRemoteAddress success');
}).catch((err: BusinessError) => {
  console.error('getRemoteAddress fail');
});
```

## getRemoteCertificate

```TypeScript
getRemoteCertificate(callback: AsyncCallback<X509CertRawData>): void
```

在TLSSocket通信连接成功之后，获取服务端的数字证书，使用callback异步回调。

**起始版本：** 9

<!--Device-TLSSocket-getRemoteCertificate(callback: AsyncCallback<X509CertRawData>): void--><!--Device-TLSSocket-getRemoteCertificate(callback: AsyncCallback<X509CertRawData>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[X509CertRawData](arkts-network-socket-x509certrawdata-t.md)&gt; | 是 | 回调函数，返回服务端的证书。失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |

## getRemoteCertificate

```TypeScript
getRemoteCertificate(): Promise<X509CertRawData>
```

在TLSSocket通信连接成功之后，获取服务端的数字证书，使用Promise异步回调。

**起始版本：** 9

<!--Device-TLSSocket-getRemoteCertificate(): Promise<X509CertRawData>--><!--Device-TLSSocket-getRemoteCertificate(): Promise<X509CertRawData>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[X509CertRawData](arkts-network-socket-x509certrawdata-t.md)&gt; | 以Promise形式返回服务端的数字证书的结果。失败返回错误码，错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |

## getSignatureAlgorithms

```TypeScript
getSignatureAlgorithms(callback: AsyncCallback<Array<string>>): void
```

在TLSSocket通信连接成功之后，获取通信双方协商后签名算法，该接口只适配双向认证模式下，使用callback异步回调。

**起始版本：** 9

<!--Device-TLSSocket-getSignatureAlgorithms(callback: AsyncCallback<Array<string>>): void--><!--Device-TLSSocket-getSignatureAlgorithms(callback: AsyncCallback<Array<string>>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;string&gt;&gt; | 是 | 回调函数，返回双方支持的签名算法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
tls.getSignatureAlgorithms((err: BusinessError, data: Array<string>) => {
  if (err) {
    console.error("getSignatureAlgorithms callback error = " + err);
  } else {
    console.info("getSignatureAlgorithms callback = " + data);
  }
});
```

## getSignatureAlgorithms

```TypeScript
getSignatureAlgorithms(): Promise<Array<string>>
```

在TLSSocket通信连接成功之后，获取通信双方协商后的签名算法，该接口只适配双向认证模式下，使用Promise异步回调。

**起始版本：** 9

<!--Device-TLSSocket-getSignatureAlgorithms(): Promise<Array<string>>--><!--Device-TLSSocket-getSignatureAlgorithms(): Promise<Array<string>>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | 以Promise形式返回获取到的双方支持的签名算法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
tls.getSignatureAlgorithms().then((data: Array<string>) => {
  console.info("getSignatureAlgorithms success" + data);
}).catch((err: BusinessError) => {
  console.error("failed" + err);
});
```

## getSocketFd

```TypeScript
getSocketFd(): Promise<int>
```

获取TLSSocket的文件描述符。使用Promise异步回调。 > **说明：** > > - bind方法调用成功后，才可调用此方法。 > > - 文件描述符的生命周期由系统管理，应用可以通过[close](#close)方法关闭Socket连接，避免直接操作 > 文件描述符进行关闭。

**起始版本：** 16

<!--Device-TLSSocket-getSocketFd(): Promise<int>--><!--Device-TLSSocket-getSocketFd(): Promise<int>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | 以Promise形式返回socket的文件描述符。 |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
let bindAddr: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
tls.bind(bindAddr, (err: BusinessError) => {
  if (err) {
    console.error('bind fail');
    return;
  }
  console.info('bind success');
});
tls.getSocketFd().then((data: number) => {
  console.info("tls socket fd: " + data);
})
```

## getState

```TypeScript
getState(callback: AsyncCallback<SocketStateBase>): void
```

在TLSSocket的bind成功之后，获取TLSSocket状态。使用callback异步回调。

**起始版本：** 9

<!--Device-TLSSocket-getState(callback: AsyncCallback<SocketStateBase>): void--><!--Device-TLSSocket-getState(callback: AsyncCallback<SocketStateBase>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[SocketStateBase](arkts-network-socket-socketstatebase-i.md)&gt; | 是 | 回调函数。成功返回TLSSocket状态，失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2303188](../errorcode-net-socket.md#2303188-非套接字的套接字操作) | Socket operation on non-socket. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
let bindAddr: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
tls.bind(bindAddr, (err: BusinessError) => {
  if (err) {
    console.error('bind fail');
    return;
  }
  console.info('bind success');
});
tls.getState((err: BusinessError, data: socket.SocketStateBase) => {
  if (err) {
    console.error('getState fail');
    return;
  }
  console.info('getState success:' + JSON.stringify(data));
});
```

## getState

```TypeScript
getState(): Promise<SocketStateBase>
```

在TLSSocket的bind成功之后，获取TLSSocket状态。使用Promise异步回调。

**起始版本：** 9

<!--Device-TLSSocket-getState(): Promise<SocketStateBase>--><!--Device-TLSSocket-getState(): Promise<SocketStateBase>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[SocketStateBase](arkts-network-socket-socketstatebase-i.md)&gt; | 以Promise形式返回获取TLSSocket状态的结果。失败返回错误码，错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2303188](../errorcode-net-socket.md#2303188-非套接字的套接字操作) | Socket operation on non-socket. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
let bindAddr: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
tls.bind(bindAddr, (err: BusinessError) => {
  if (err) {
    console.error('bind fail');
    return;
  }
  console.info('bind success');
});
tls.getState().then(() => {
  console.info('getState success');
}).catch((err: BusinessError) => {
  console.error('getState fail');
});
```

## off('connect' | 'close')

```TypeScript
off(type: 'connect' | 'close', callback?: Callback<void>): void
```

取消订阅TLSSocket的连接事件或关闭事件。使用callback异步回调。

**起始版本：** 9

<!--Device-TLSSocket-off(type: 'connect' | 'close', callback?: Callback<void>): void--><!--Device-TLSSocket-off(type: 'connect' | 'close', callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'connect' \| 'close' | 是 | 订阅的事件类型。&lt;br /&gt;- 'connect'：连接事件。&lt;br /&gt;- 'close'：关闭事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | 回调函数。TLSSocket连接订阅某类事件触发的调用函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
let callback1 = () => {
  console.info("on connect success");
}
tls.on('connect', callback1);
// 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。
tls.off('connect', callback1);
tls.off('connect');
let callback2 = () => {
  console.info("on close success");
}
tls.on('close', callback2);
// 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。
tls.off('close', callback2);
```

## off('connect' | 'close')

```TypeScript
off(type: 'connect' | 'close', callback?: Callback<void>): void
```

取消订阅TLSSocket的连接事件或关闭事件。使用callback异步回调。

**起始版本：** 9

<!--Device-TLSSocket-off(type: 'connect' | 'close', callback?: Callback<void>): void--><!--Device-TLSSocket-off(type: 'connect' | 'close', callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'connect' \| 'close' | 是 | 订阅的事件类型。&lt;br /&gt;- 'connect'：连接事件。&lt;br /&gt;- 'close'：关闭事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | 回调函数。TLSSocket连接订阅某类事件触发的调用函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
let callback1 = () => {
  console.info("on connect success");
}
tls.on('connect', callback1);
// 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。
tls.off('connect', callback1);
tls.off('connect');
let callback2 = () => {
  console.info("on close success");
}
tls.on('close', callback2);
// 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。
tls.off('close', callback2);
```

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

取消订阅TLSSocket连接的error事件。使用callback异步回调。

**起始版本：** 9

<!--Device-TLSSocket-off(type: 'error', callback?: ErrorCallback): void--><!--Device-TLSSocket-off(type: 'error', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 订阅的事件类型。'error'：error事件。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-errorcallback-t.md) | 否 | 回调函数。TLSSocket连接取消订阅某类error事件触发的调用函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
let callback = (err: BusinessError) => {
  console.error("on error, err:" + JSON.stringify(err));
}
tls.on('error', callback);
// 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。
tls.off('error', callback);
```

## off('message')

```TypeScript
off(type: 'message', callback?: Callback<SocketMessageInfo>): void
```

取消订阅TLSSocket连接的接收消息事件。使用callback异步回调。

**起始版本：** 9

<!--Device-TLSSocket-off(type: 'message', callback?: Callback<SocketMessageInfo>): void--><!--Device-TLSSocket-off(type: 'message', callback?: Callback<SocketMessageInfo>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'message' | 是 | 订阅的事件类型。'message'：接收消息事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[SocketMessageInfo](arkts-network-socket-socketmessageinfo-i.md)&gt; | 否 | 回调函数。TLSSocket连接取消订阅某类接受消息事件触发的调用函数，返回TLSSocket连接信息。<br>**起始版本：** 11 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
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
tls.on('message', callback);
// 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。
tls.off('message', callback);
```

## on('connect' | 'close')

```TypeScript
on(type: 'connect' | 'close', callback: Callback<void>): void
```

订阅TLSSocket的连接事件或关闭事件。使用callback异步回调。 > **说明：** > > bind方法调用成功后，才可调用此方法。

**起始版本：** 9

<!--Device-TLSSocket-on(type: 'connect' | 'close', callback: Callback<void>): void--><!--Device-TLSSocket-on(type: 'connect' | 'close', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'connect' \| 'close' | 是 | 订阅的事件类型。&lt;br /&gt;- 'connect'：连接事件。&lt;br /&gt;- 'close'：关闭事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | 回调函数。TLSSocket连接订阅某类事件触发的调用函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
let bindAddr: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
tls.bind(bindAddr, (err: BusinessError) => {
  if (err) {
    console.error('bind fail');
    return;
  }
  console.info('bind success');
  tls.on('connect', () => {
    console.info("on connect success")
  });
  tls.on('close', () => {
    console.info("on close success")
  });
});
```

## on('connect' | 'close')

```TypeScript
on(type: 'connect' | 'close', callback: Callback<void>): void
```

订阅TLSSocket的连接事件或关闭事件。使用callback异步回调。 > **说明：** > > bind方法调用成功后，才可调用此方法。

**起始版本：** 9

<!--Device-TLSSocket-on(type: 'connect' | 'close', callback: Callback<void>): void--><!--Device-TLSSocket-on(type: 'connect' | 'close', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'connect' \| 'close' | 是 | 订阅的事件类型。&lt;br /&gt;- 'connect'：连接事件。&lt;br /&gt;- 'close'：关闭事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | 回调函数。TLSSocket连接订阅某类事件触发的调用函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
let bindAddr: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
tls.bind(bindAddr, (err: BusinessError) => {
  if (err) {
    console.error('bind fail');
    return;
  }
  console.info('bind success');
  tls.on('connect', () => {
    console.info("on connect success")
  });
  tls.on('close', () => {
    console.info("on close success")
  });
});
```

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

订阅TLSSocket连接的error事件。使用callback异步回调。 > **说明：** > > bind方法调用成功后，才可调用此方法。

**起始版本：** 9

<!--Device-TLSSocket-on(type: 'error', callback: ErrorCallback): void--><!--Device-TLSSocket-on(type: 'error', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 订阅的事件类型。'error'：error事件。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-errorcallback-t.md) | 是 | 回调函数。TLSSocket连接订阅某类error事件触发的调用函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
let bindAddr: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
tls.bind(bindAddr, (err: BusinessError) => {
  if (err) {
    console.error('bind fail');
    return;
  }
  console.info('bind success');
  tls.on('error', (err: BusinessError) => {
    console.error("on error, err:" + JSON.stringify(err))
  });
});
```

## on('message')

```TypeScript
on(type: 'message', callback: Callback<SocketMessageInfo>): void
```

订阅TLSSocket连接的接收消息事件。使用callback异步回调。 > **说明：** > > bind方法调用成功后，才可调用此方法。

**起始版本：** 9

<!--Device-TLSSocket-on(type: 'message', callback: Callback<SocketMessageInfo>): void--><!--Device-TLSSocket-on(type: 'message', callback: Callback<SocketMessageInfo>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'message' | 是 | 订阅的事件类型。'message'：接收消息事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[SocketMessageInfo](arkts-network-socket-socketmessageinfo-i.md)&gt; | 是 | 回调函数。TLSSocket连接订阅某类接受消息事件触发的调用函数，返回TLSSocket连接信息。<br>**起始版本：** 11 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
let bindAddr: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
tls.bind(bindAddr, (err: BusinessError) => {
  if (err) {
    console.error('bind fail');
    return;
  }
  console.info('bind success');
  tls.on('message', (value: socket.SocketMessageInfo) => {
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
send(data: string | ArrayBuffer, callback: AsyncCallback<void>): void
```

在TLSSocket通信连接成功之后，向服务端发送消息，使用callback异步回调。

**起始版本：** 9

<!--Device-TLSSocket-send(data: string | ArrayBuffer, callback: AsyncCallback<void>): void--><!--Device-TLSSocket-send(data: string | ArrayBuffer, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string \| ArrayBuffer | 是 | 发送的数据内容。<br>**起始版本：** 9 - 11 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数,返回TLSSocket发送数据的结果。失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2303506](../errorcode-net-socket.md#2303506-关闭tls连接失败) | Failed to close the TLS connection. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2303505](../errorcode-net-socket.md#2303505-tls系统调用错误) | An error occurred in the TLS system call. |
| [2303503](../errorcode-net-socket.md#2303503-tls写入错误) | An error occurred when writing data on the TLS socket. |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
tls.send("xxxx", (err: BusinessError) => {
  if (err) {
    console.error("send callback error = " + err);
  } else {
    console.info("send success");
  }
});
```

## send

```TypeScript
send(data: string | ArrayBuffer): Promise<void>
```

在TLSSocket通信连接成功之后，向服务端发送消息，使用Promise异步回调。

**起始版本：** 9

<!--Device-TLSSocket-send(data: string | ArrayBuffer): Promise<void>--><!--Device-TLSSocket-send(data: string | ArrayBuffer): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string \| ArrayBuffer | 是 | 发送的数据内容。<br>**起始版本：** 9 - 11 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 以Promise形式返回,返回TLSSocket发送数据的结果。失败返回错误码，错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2303506](../errorcode-net-socket.md#2303506-关闭tls连接失败) | Failed to close the TLS connection. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2303505](../errorcode-net-socket.md#2303505-tls系统调用错误) | An error occurred in the TLS system call. |
| [2303503](../errorcode-net-socket.md#2303503-tls写入错误) | An error occurred when writing data on the TLS socket. |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
tls.send("xxxx").then(() => {
  console.info("send success");
}).catch((err: BusinessError) => {
  console.error("failed" + err);
});
```

## setExtraOptions

```TypeScript
setExtraOptions(options: TCPExtraOptions, callback: AsyncCallback<void>): void
```

在TLSSocket的bind成功之后，设置TCPSocket连接的其他属性。使用callback异步回调。

**起始版本：** 9

<!--Device-TLSSocket-setExtraOptions(options: TCPExtraOptions, callback: AsyncCallback<void>): void--><!--Device-TLSSocket-setExtraOptions(options: TCPExtraOptions, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TCPExtraOptions](arkts-network-socket-tcpextraoptions-i.md) | 是 | TCPSocket连接的其他属性，参考[TCPExtraOptions](arkts-network-socket-tcpextraoptions-i.md)。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。成功返回设置TCPSocket连接的其他属性的结果，失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2303188](../errorcode-net-socket.md#2303188-非套接字的套接字操作) | Socket operation on non-socket. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
let bindAddr: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
tls.bind(bindAddr, (err: BusinessError) => {
  if (err) {
    console.error('bind fail');
    return;
  }
  console.info('bind success');
});

interface SocketLinger {
  on: boolean;
  linger: number;
}

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
tls.setExtraOptions(tcpExtraOptions, (err: BusinessError) => {
  if (err) {
    console.error('setExtraOptions fail');
    return;
  }
  console.info('setExtraOptions success');
});
```

## setExtraOptions

```TypeScript
setExtraOptions(options: TCPExtraOptions): Promise<void>
```

在TLSSocket的bind成功之后，设置TCPSocket连接的其他属性。使用Promise异步回调。

**起始版本：** 9

<!--Device-TLSSocket-setExtraOptions(options: TCPExtraOptions): Promise<void>--><!--Device-TLSSocket-setExtraOptions(options: TCPExtraOptions): Promise<void>-End-->

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
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2303188](../errorcode-net-socket.md#2303188-非套接字的套接字操作) | Socket operation on non-socket. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
let bindAddr: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
tls.bind(bindAddr, (err: BusinessError) => {
  if (err) {
    console.error('bind fail');
    return;
  }
  console.info('bind success');
});

interface SocketLinger {
  on: boolean;
  linger: number;
}

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
tls.setExtraOptions(tcpExtraOptions).then(() => {
  console.info('setExtraOptions success');
}).catch((err: BusinessError) => {
  console.error('setExtraOptions fail');
});
```

