# TLSSocketServer

TLSSocketServer连接。在调用TLSSocketServer的方法前，需要先通过 [socket.constructTLSSocketServerInstance](arkts-network-socket-constructtlssocketserverinstance-f.md)创建TLSSocketServer对象。

**起始版本：** 10

<!--Device-socket-export interface TLSSocketServer--><!--Device-socket-export interface TLSSocketServer-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## close

```TypeScript
close(): Promise<void>
```

TLSSocketServer停止监听并释放通过[listen](arkts-network-socket-tcpsocketserver-i.md#listen)方法绑定的端口。使用Promise异步回调。 > **说明：** > > 该方法不会关闭已有连接。如需关闭，请调用[TLSSocketConnection](arkts-network-socket-tlssocketconnection-i.md)的 > [close](arkts-network-socket-tcpsocketconnection-i.md#close)方法。

**起始版本：** 20

**需要权限：** ohos.permission.INTERNET

<!--Device-TLSSocketServer-close(): Promise<void>--><!--Device-TLSSocketServer-close(): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tlsServer: socket.TLSSocketServer = socket.constructTLSSocketServerInstance();
let netAddress: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let tlsSecureOptions: socket.TLSSecureOptions = {
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
  address: netAddress,
  secureOptions: tlsSecureOptions,
  ALPNProtocols: ["spdy/1", "http/1.1"]
}
tlsServer.on('connect', (connection: socket.TLSSocketConnection) => {
  console.info("connection clientId: " + connection.clientId);
  // 逻辑处理
  tlsServer.close(); // 停止监听
  connection.close(); // 关闭当前连接
});
tlsServer.listen(tlsConnectOptions).then(() => {
  console.info("listen callback success");
}).catch((err: BusinessError) => {
  console.error("listen failed: " + err.code);
});
```

## getCertificate

```TypeScript
getCertificate(callback: AsyncCallback<X509CertRawData>): void
```

在TLSSocketServer通信连接成功之后，获取本地的数字证书，使用callback异步回调。 > **说明：** > > listen方法调用成功后，才可调用此方法。

**起始版本：** 10

<!--Device-TLSSocketServer-getCertificate(callback: AsyncCallback<X509CertRawData>): void--><!--Device-TLSSocketServer-getCertificate(callback: AsyncCallback<X509CertRawData>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[X509CertRawData](arkts-network-socket-x509certrawdata-t.md)&gt; | 是 | 回调函数，成功返回本地的证书，失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2303504](../errorcode-net-socket.md#2303504-查找x509时出错) | An error occurred when verifying the X.509 certificate. |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |

## getCertificate

```TypeScript
getCertificate(): Promise<X509CertRawData>
```

在TLSSocketServer通信连接之后，获取本地的数字证书，使用Promise异步回调。 > **说明：** > > listen方法调用成功后，才可调用此方法。

**起始版本：** 10

<!--Device-TLSSocketServer-getCertificate(): Promise<X509CertRawData>--><!--Device-TLSSocketServer-getCertificate(): Promise<X509CertRawData>-End-->

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

## getLocalAddress

```TypeScript
getLocalAddress(): Promise<NetAddress>
```

获取TLSSocketServer的本地Socket地址。使用Promise异步回调。 > **说明：** > > 在TLSSocketServer通信连接成功之后，才可调用此方法。

**起始版本：** 12

<!--Device-TLSSocketServer-getLocalAddress(): Promise<NetAddress>--><!--Device-TLSSocketServer-getLocalAddress(): Promise<NetAddress>-End-->

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

let tlsServer: socket.TLSSocketServer = socket.constructTLSSocketServerInstance();
tlsServer.getLocalAddress().then((localAddress: socket.NetAddress) => {
  console.info("Get success: " + JSON.stringify(localAddress));
}).catch((err: BusinessError) => {
  console.error("Get failed, error: " + JSON.stringify(err));
})
```

## getProtocol

```TypeScript
getProtocol(callback: AsyncCallback<string>): void
```

在TLSSocketServer通信连接成功之后，获取通信的协议版本，使用callback异步回调。 > **说明：** > > listen方法调用成功后，才可调用此方法。

**起始版本：** 10

<!--Device-TLSSocketServer-getProtocol(callback: AsyncCallback<string>): void--><!--Device-TLSSocketServer-getProtocol(callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;string&gt; | 是 | 回调函数，返回通信的协议。失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2303505](../errorcode-net-socket.md#2303505-tls系统调用错误) | An error occurred in the TLS system call. |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tlsServer: socket.TLSSocketServer = socket.constructTLSSocketServerInstance();
let netAddress: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let tlsSecureOptions: socket.TLSSecureOptions = {
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
  address: netAddress,
  secureOptions: tlsSecureOptions,
  ALPNProtocols: ["spdy/1", "http/1.1"]
}
tlsServer.listen(tlsConnectOptions).then(() => {
  console.info("listen callback success");
}).catch((err: BusinessError) => {
  console.error("failed: " + JSON.stringify(err));
});
tlsServer.getProtocol((err: BusinessError, data: string) => {
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

在TLSSocketServer通信连接成功之后，获取通信的协议版本，使用Promise异步回调。 > **说明：** > > listen方法调用成功后，才可调用此方法。

**起始版本：** 10

<!--Device-TLSSocketServer-getProtocol(): Promise<string>--><!--Device-TLSSocketServer-getProtocol(): Promise<string>-End-->

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

let tlsServer: socket.TLSSocketServer = socket.constructTLSSocketServerInstance();
let netAddress: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let tlsSecureOptions: socket.TLSSecureOptions = {
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
  address: netAddress,
  secureOptions: tlsSecureOptions,
  ALPNProtocols: ["spdy/1", "http/1.1"]
}
tlsServer.listen(tlsConnectOptions).then(() => {
  console.info("listen callback success");
}).catch((err: BusinessError) => {
  console.error("failed: " + JSON.stringify(err));
});
tlsServer.getProtocol().then((data: string) => {
  console.info(data);
}).catch((err: BusinessError) => {
  console.error("failed" + err);
});
```

## getSocketFd

```TypeScript
getSocketFd(): Promise<int>
```

获取TLSSocketServer监听端口绑定的文件描述符。使用Promise异步回调。 > **说明：** > > - [listen](arkts-network-socket-tcpsocketserver-i.md#listen)方法调用成功后，才可调用此方法。多次调用listen时，会获取最新监听端口绑定的文件描述符。 > > - 监听异常、Socket已关闭（如调用close后）等异常情况下调用本接口会返回-1。 > > - 文件描述符的生命周期由系统管理，应用可以通过[close](arkts-network-socket-tcpsocketserver-i.md#close)方法关闭Socket连接，避免直接操作文件描述符进行关闭。

**起始版本：** 23

**需要权限：** ohos.permission.INTERNET

<!--Device-TLSSocketServer-getSocketFd(): Promise<int>--><!--Device-TLSSocketServer-getSocketFd(): Promise<int>-End-->

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

let tlsServer: socket.TLSSocketServer = socket.constructTLSSocketServerInstance();
let netAddress: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let tlsSecureOptions: socket.TLSSecureOptions = {
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
  address: netAddress,
  secureOptions: tlsSecureOptions,
  ALPNProtocols: ["spdy/1", "http/1.1"]
}
tlsServer.listen(tlsConnectOptions).then(() => {
  console.info("listen success");
  tlsServer.getSocketFd().then((fd: number) => {
    console.info(`Socket FD：${fd}`);
  }).catch((err: BusinessError) => {
    console.error(`getSocketFd fail: ${err.message}, errorCode: ${err.code}`);
  });
}).catch((err: BusinessError) => {
  console.error(`listen failed: ${JSON.stringify(err)}`);
});
```

## getState

```TypeScript
getState(callback: AsyncCallback<SocketStateBase>): void
```

在TLSSocketServer的listen成功之后，获取TLSSocketServer状态。使用callback异步回调。 > **说明：** > > listen方法调用成功后，才可调用此方法。

**起始版本：** 10

<!--Device-TLSSocketServer-getState(callback: AsyncCallback<SocketStateBase>): void--><!--Device-TLSSocketServer-getState(callback: AsyncCallback<SocketStateBase>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[SocketStateBase](arkts-network-socket-socketstatebase-i.md)&gt; | 是 | 回调函数。成功返回TLSSocketServer状态，失败返回错误码、错误信息。 |

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

let tlsServer: socket.TLSSocketServer = socket.constructTLSSocketServerInstance();
let netAddress: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let tlsSecureOptions: socket.TLSSecureOptions = {
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
  address: netAddress,
  secureOptions: tlsSecureOptions,
  ALPNProtocols: ["spdy/1", "http/1.1"]
}
tlsServer.listen(tlsConnectOptions).then(() => {
  console.info("listen callback success");
}).catch((err: BusinessError) => {
  console.error("failed: " + JSON.stringify(err));
});
tlsServer.getState((err: BusinessError, data: socket.SocketStateBase) => {
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

在TLSSocketServer的listen成功之后，获取TLSSocketServer状态。使用Promise异步回调。 > **说明：** > > listen方法调用成功后，才可调用此方法。

**起始版本：** 10

<!--Device-TLSSocketServer-getState(): Promise<SocketStateBase>--><!--Device-TLSSocketServer-getState(): Promise<SocketStateBase>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[SocketStateBase](arkts-network-socket-socketstatebase-i.md)&gt; | 以Promise形式返回获取TLSSocketServer状态的结果。失败返回错误码，错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2303188](../errorcode-net-socket.md#2303188-非套接字的套接字操作) | Socket operation on non-socket. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tlsServer: socket.TLSSocketServer = socket.constructTLSSocketServerInstance();
let netAddress: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let tlsSecureOptions: socket.TLSSecureOptions = {
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
  address: netAddress,
  secureOptions: tlsSecureOptions,
  ALPNProtocols: ["spdy/1", "http/1.1"]
}
tlsServer.listen(tlsConnectOptions).then(() => {
  console.info("listen callback success");
}).catch((err: BusinessError) => {
  console.error("failed: " + JSON.stringify(err));
});
tlsServer.getState().then(() => {
  console.info('getState success');
}).catch((err: BusinessError) => {
  console.error('getState fail');
});
```

## listen

```TypeScript
listen(options: TLSConnectOptions, callback: AsyncCallback<void>): void
```

绑定IP地址和端口，在TLSSocketServer上bind成功之后，监听客户端的连接，创建和初始化TLS会话，实现建立连接过程，加载证书秘钥并验证，使用callback异步回调。 > **注意：** > > IP地址设置为0.0.0.0时，可以监听本机所有地址。

**起始版本：** 10

**需要权限：** ohos.permission.INTERNET

<!--Device-TLSSocketServer-listen(options: TLSConnectOptions, callback: AsyncCallback<void>): void--><!--Device-TLSSocketServer-listen(options: TLSConnectOptions, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TLSConnectOptions](arkts-network-socket-tlsconnectoptions-i.md) | 是 | TLSSocketServer连接所需要的参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数，成功返回空，失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2303506](../errorcode-net-socket.md#2303506-关闭tls连接失败) | Failed to close the TLS connection. |
| [2303505](../errorcode-net-socket.md#2303505-tls系统调用错误) | An error occurred in the TLS system call. |
| [2303111](../errorcode-net-socket.md#2303111-资源暂时不可用请重试) | Resource temporarily unavailable. Try again. |
| [2303109](../errorcode-net-socket.md#2303109-错误文件编号) | Bad file number. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2303199](../errorcode-net-socket.md#2303199-不能分配请求的地址) | Cannot assign requested address. |
| [2303503](../errorcode-net-socket.md#2303503-tls写入错误) | An error occurred when writing data on the TLS socket. |
| [2303198](../errorcode-net-socket.md#2303198-网络地址已被使用) | Address already in use. |
| [2303502](../errorcode-net-socket.md#2303502-tls读取错误) | An error occurred when reading data on the TLS socket. |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tlsServer: socket.TLSSocketServer = socket.constructTLSSocketServerInstance();
let netAddress: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let tlsSecureOptions: socket.TLSSecureOptions = {
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
  address: netAddress,
  secureOptions: tlsSecureOptions,
  ALPNProtocols: ["spdy/1", "http/1.1"],
  skipRemoteValidation: false
}
tlsServer.listen(tlsConnectOptions, (err: BusinessError) => {
  console.error("listen callback error" + err);
});
```

## listen

```TypeScript
listen(options: TLSConnectOptions): Promise<void>
```

绑定IP地址和端口，在TLSSocketServer上bind成功之后，监听客户端的连接，并创建和初始化TLS会话，实现建立连接过程，加载证书秘钥并验证，使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.INTERNET

<!--Device-TLSSocketServer-listen(options: TLSConnectOptions): Promise<void>--><!--Device-TLSSocketServer-listen(options: TLSConnectOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TLSConnectOptions](arkts-network-socket-tlsconnectoptions-i.md) | 是 | 连接所需要的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 以Promise形式返回，成功返回空，失败返回错误码，错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2303506](../errorcode-net-socket.md#2303506-关闭tls连接失败) | Failed to close the TLS connection. |
| [2303505](../errorcode-net-socket.md#2303505-tls系统调用错误) | An error occurred in the TLS system call. |
| [2303111](../errorcode-net-socket.md#2303111-资源暂时不可用请重试) | Resource temporarily unavailable. Try again. |
| [2303109](../errorcode-net-socket.md#2303109-错误文件编号) | Bad file number. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2303199](../errorcode-net-socket.md#2303199-不能分配请求的地址) | Cannot assign requested address. |
| [2303503](../errorcode-net-socket.md#2303503-tls写入错误) | An error occurred when writing data on the TLS socket. |
| [2303198](../errorcode-net-socket.md#2303198-网络地址已被使用) | Address already in use. |
| [2303502](../errorcode-net-socket.md#2303502-tls读取错误) | An error occurred when reading data on the TLS socket. |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tlsServer: socket.TLSSocketServer = socket.constructTLSSocketServerInstance();
let netAddress: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let tlsSecureOptions: socket.TLSSecureOptions = {
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
  address: netAddress,
  secureOptions: tlsSecureOptions,
  ALPNProtocols: ["spdy/1", "http/1.1"],
  skipRemoteValidation: false
}
tlsServer.listen(tlsConnectOptions).then(() => {
  console.info("listen callback success");
}).catch((err: BusinessError) => {
  console.error("failed: " + JSON.stringify(err));
});
```

## off('connect')

```TypeScript
off(type: 'connect', callback?: Callback<TLSSocketConnection>): void
```

取消订阅TLSSocketServer的连接事件。使用callback异步回调。 > **说明：** > > listen方法调用成功后，才可调用此方法。 > > 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。

**起始版本：** 10

<!--Device-TLSSocketServer-off(type: 'connect', callback?: Callback<TLSSocketConnection>): void--><!--Device-TLSSocketServer-off(type: 'connect', callback?: Callback<TLSSocketConnection>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'connect' | 是 | 订阅的事件类型。'connect'：连接事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[TLSSocketConnection](arkts-network-socket-tlssocketconnection-i.md)&gt; | 否 | 回调函数。失败时返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tlsServer: socket.TLSSocketServer = socket.constructTLSSocketServerInstance();
let netAddress: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let tlsSecureOptions: socket.TLSSecureOptions = {
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
  address: netAddress,
  secureOptions: tlsSecureOptions,
  ALPNProtocols: ["spdy/1", "http/1.1"]
}
tlsServer.listen(tlsConnectOptions).then(() => {
  console.info("listen callback success");
}).catch((err: BusinessError) => {
  console.error("failed: " + JSON.stringify(err));
});

let callback = (data: socket.TLSSocketConnection) => {
  console.info('on connect message: ' + JSON.stringify(data));
}
tlsServer.on('connect', callback);
// 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。
tlsServer.off('connect', callback);
tlsServer.off('connect');
```

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

取消订阅TLSSocketServer连接的error事件。使用callback异步回调。 > **说明：** > > listen方法调用成功后，才可调用此方法。 > > 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。

**起始版本：** 10

<!--Device-TLSSocketServer-off(type: 'error', callback?: ErrorCallback): void--><!--Device-TLSSocketServer-off(type: 'error', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 订阅的事件类型。'error'：error事件。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-errorcallback-t.md) | 否 | 回调函数。失败时返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tlsServer: socket.TLSSocketServer = socket.constructTLSSocketServerInstance();
let netAddress: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let tlsSecureOptions: socket.TLSSecureOptions = {
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
  address: netAddress,
  secureOptions: tlsSecureOptions,
  ALPNProtocols: ["spdy/1", "http/1.1"]
}
tlsServer.listen(tlsConnectOptions).then(() => {
  console.info("listen callback success");
}).catch((err: BusinessError) => {
  console.error("failed: " + JSON.stringify(err));
});

let callback = (err: BusinessError) => {
  console.error("on error, err:" + JSON.stringify(err));
}
tlsServer.on('error', callback);
// 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。
tlsServer.off('error', callback);
tlsServer.off('error');
```

## on('connect')

```TypeScript
on(type: 'connect', callback: Callback<TLSSocketConnection>): void
```

订阅TLSSocketServer的连接事件。使用callback异步回调。 > **说明：** > > listen方法调用成功后，才可调用此方法。

**起始版本：** 10

<!--Device-TLSSocketServer-on(type: 'connect', callback: Callback<TLSSocketConnection>): void--><!--Device-TLSSocketServer-on(type: 'connect', callback: Callback<TLSSocketConnection>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'connect' | 是 | 订阅的事件类型。'connect'：连接事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[TLSSocketConnection](arkts-network-socket-tlssocketconnection-i.md)&gt; | 是 | 回调函数。失败时返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tlsServer: socket.TLSSocketServer = socket.constructTLSSocketServerInstance();
let netAddress: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let tlsSecureOptions: socket.TLSSecureOptions = {
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
  address: netAddress,
  secureOptions: tlsSecureOptions,
  ALPNProtocols: ["spdy/1", "http/1.1"]
}
tlsServer.listen(tlsConnectOptions).then(() => {
  console.info("listen callback success");
  tlsServer.on('connect', (data: socket.TLSSocketConnection) => {
    console.info(JSON.stringify(data));
  });
}).catch((err: BusinessError) => {
  console.error("failed: " + JSON.stringify(err));
});
```

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

订阅TLSSocketServer连接的error事件。使用callback异步回调。 > **说明：** > > listen方法调用成功后，才可调用此方法。

**起始版本：** 10

<!--Device-TLSSocketServer-on(type: 'error', callback: ErrorCallback): void--><!--Device-TLSSocketServer-on(type: 'error', callback: ErrorCallback): void-End-->

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

let tlsServer: socket.TLSSocketServer = socket.constructTLSSocketServerInstance();
let netAddress: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let tlsSecureOptions: socket.TLSSecureOptions = {
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
  address: netAddress,
  secureOptions: tlsSecureOptions,
  ALPNProtocols: ["spdy/1", "http/1.1"]
}
tlsServer.listen(tlsConnectOptions).then(() => {
  console.info("listen callback success");
}).catch((err: BusinessError) => {
  console.error("failed: " + JSON.stringify(err));
});
tlsServer.on('error', (err: BusinessError) => {
  console.error("on error, err:" + JSON.stringify(err))
});
```

## setExtraOptions

```TypeScript
setExtraOptions(options: TCPExtraOptions, callback: AsyncCallback<void>): void
```

在TLSSocketServer的listen成功之后，设置TLSSocketServer连接的其他属性。使用callback异步回调。 > **说明：** > > listen方法调用成功后，才可调用此方法。

**起始版本：** 10

<!--Device-TLSSocketServer-setExtraOptions(options: TCPExtraOptions, callback: AsyncCallback<void>): void--><!--Device-TLSSocketServer-setExtraOptions(options: TCPExtraOptions, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TCPExtraOptions](arkts-network-socket-tcpextraoptions-i.md) | 是 | TLSSocketServer连接的其他属性。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。成功返回空，失败返回错误码、错误信息。 |

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

let tlsServer: socket.TLSSocketServer = socket.constructTLSSocketServerInstance();
let netAddress: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let tlsSecureOptions: socket.TLSSecureOptions = {
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
  address: netAddress,
  secureOptions: tlsSecureOptions,
  ALPNProtocols: ["spdy/1", "http/1.1"]
}
tlsServer.listen(tlsConnectOptions).then(() => {
  console.info("listen callback success");
}).catch((err: BusinessError) => {
  console.error("failed: " + JSON.stringify(err));
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
  socketTimeout: 3000
}
tlsServer.setExtraOptions(tcpExtraOptions, (err: BusinessError) => {
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

在TLSSocketServer的listen成功之后，设置TLSSocketServer连接的其他属性，使用Promise异步回调。 > **说明：** > > listen方法调用成功后，才可调用此方法。

**起始版本：** 10

<!--Device-TLSSocketServer-setExtraOptions(options: TCPExtraOptions): Promise<void>--><!--Device-TLSSocketServer-setExtraOptions(options: TCPExtraOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TCPExtraOptions](arkts-network-socket-tcpextraoptions-i.md) | 是 | TLSSocketServer连接的其他属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 以Promise形式返回，成功返回空，失败返回错误码，错误信息。 |

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

let tlsServer: socket.TLSSocketServer = socket.constructTLSSocketServerInstance();
let netAddress: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
let tlsSecureOptions: socket.TLSSecureOptions = {
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
  address: netAddress,
  secureOptions: tlsSecureOptions,
  ALPNProtocols: ["spdy/1", "http/1.1"]
}
tlsServer.listen(tlsConnectOptions).then(() => {
  console.info("listen callback success");
}).catch((err: BusinessError) => {
  console.error("failed: " + JSON.stringify(err));
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
  socketTimeout: 3000
}
tlsServer.setExtraOptions(tcpExtraOptions).then(() => {
  console.info('setExtraOptions success');
}).catch((err: BusinessError) => {
  console.error('setExtraOptions fail');
});
```

