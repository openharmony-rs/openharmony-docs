# TLSSocket

TLSSocket连接。在调用TLSSocket的方法前，需要先通过[socket.constructTLSSocketInstance](arkts-network-socket-constructtlssocketinstance-f.md)创建 TLSSocket对象。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## bind

```TypeScript
bind(address: NetAddress, callback: AsyncCallback<void>): void
```

绑定IP地址和端口。使用callback异步回调。

> **说明：**
> 
> 如果TLSSocket对象是通过TCPSocket对象升级创建的，可以不用执行bind方法。

**起始版本：** 9

**需要权限：** ohos.permission.INTERNET

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| address | NetAddress | 是 | 本端地址信息，参考 [NetAddress](../../../reference/apis-network-kit/js-apis-socket.md#netaddress)。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。成功返回TLSSocket绑定本机的IP地址和端口的结果。失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2303198](../errorcode-net-socket.md#2303198-网络地址已被使用) | Address already in use. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let udp: socket.UDPSocket = socket.constructUDPSocketInstance();
let bindAddr: socket.NetAddress = {
  address: '192.168.xx.xxx',  // 本端地址
  port: 1234
}
udp.bind(bindAddr, (err: BusinessError) => {
  if (err) {
    console.error('bind fail');
    return;
  }
  console.info('bind success');
});
```

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

绑定IP地址和端口。使用Promise异步回调。

> **说明：**
> 
> 如果TLSSocket对象是通过TCPSocket对象升级创建的，可以不用执行bind方法。

**起始版本：** 9

**需要权限：** ohos.permission.INTERNET

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| address | NetAddress | 是 | 本端地址信息，参考 [NetAddress](../../../reference/apis-network-kit/js-apis-socket.md#netaddress)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 以Promise形式返回TLSSocket绑定本机的IP地址和端口的结果。失败返回错误码，错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2303198](../errorcode-net-socket.md#2303198-网络地址已被使用) | Address already in use. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let udp: socket.UDPSocket = socket.constructUDPSocketInstance();
let bindAddr: socket.NetAddress = {
  address: '192.168.xx.xxx',  // 本端地址
  port: 8080
}
udp.bind(bindAddr).then(() => {
  console.info('bind success');
}).catch((err: BusinessError) => {
  console.error('bind fail');
});
```

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

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数,成功返回TLSSocket关闭连接的结果。失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |
| [2303505](../errorcode-net-socket.md#2303505-tls系统调用错误) | An error occurred in the TLS system call. |
| [2303506](../errorcode-net-socket.md#2303506-关闭tls连接失败) | Failed to close the TLS connection. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let udp: socket.UDPSocket = socket.constructUDPSocketInstance();
udp.close((err: BusinessError) => {
  if (err) {
    console.error('close fail');
    return;
  }
  console.info('close success');
})
```

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
  console.error("failed" + err);
});

tlsServer.on('connect', (client: socket.TLSSocketConnection) => {
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

在TLSSocket通信连接成功之后，断开连接，使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 以Promise形式返回,返回TLSSocket关闭连接的结果。失败返回错误码，错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |
| [2303505](../errorcode-net-socket.md#2303505-tls系统调用错误) | An error occurred in the TLS system call. |
| [2303506](../errorcode-net-socket.md#2303506-关闭tls连接失败) | Failed to close the TLS connection. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let udp: socket.UDPSocket = socket.constructUDPSocketInstance();
udp.close().then(() => {
  console.info('close success');
}).catch((err: BusinessError) => {
  console.error('close fail');
});
```

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

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcpServer: socket.TCPSocketServer = socket.constructTCPSocketServerInstance();
let listenAddr: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080,
  family: 1
}
tcpServer.on('connect', (connection: socket.TCPSocketConnection) => {
  console.info("connection clientId: " + connection.clientId);
  // 逻辑处理
  tcpServer.close(); // 停止监听
  connection.close(); // 关闭当前连接
});
tcpServer.listen(listenAddr).then(() => {
  console.info('listen success');
}).catch((err: BusinessError) => {
  console.error('listen fail: ' + err.code);
});
```

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

```TypeScript
import { socket } from '@kit.NetworkKit';

let client: socket.LocalSocket = socket.constructLocalSocketInstance();

client.close().then(() => {
  console.info('close success');
}).catch((err: Object) => {
  console.error('close fail: ' + JSON.stringify(err));
});
```

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { socket } from '@kit.NetworkKit';
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let localserver: socket.LocalSocketServer = socket.constructLocalSocketServerInstance();
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let sandboxPath: string = context.filesDir + '/testSocket';
let addr: socket.LocalAddress = {
  address: sandboxPath
}
localserver.on('connect', (connection: socket.LocalSocketConnection) => {
  console.info("connection clientId: " + connection.clientId);
  // 逻辑处理
  localserver.close(); // 停止监听
  connection.close(); // 关闭当前连接
});
localserver.listen(addr).then(() => {
  console.info('listen success');
}).catch((err: BusinessError) => {
  console.error('listen fail: ' + err.code);
});
```

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
  console.error("failed" + err);
});
tlsServer.on('connect', (client: socket.TLSSocketConnection) => {
  client.close().then(() => {
    console.info('close success');
  }).catch((err: BusinessError) => {
    console.error('close fail');
  });
});
```

## connect

```TypeScript
connect(options: TLSConnectOptions, callback: AsyncCallback<void>): void
```

在TLSSocket上bind成功之后，进行通信连接，并创建和初始化TLS会话，实现建立连接过程，启动与服务器的TLS/SSL握手，实现数据传输功能，使用callback异步回调。需要注意options入参下 secureOptions内的ca在API11及之前的版本为必填项，需填入服务端的ca证书(用于认证校验服务端的数字证书)，证书内容以"-----BEGIN CERTIFICATE-----"开头，以"-----END CERTIFICATE-----"结尾，自API12开始，为非必填项。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TLSConnectOptions](arkts-network-socket-tlsconnectoptions-i.md) | 是 | TLSSocket连接所需要的参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，成功无返回，失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2303104](../errorcode-net-socket.md#2303104-中断系统调用) | Interrupted system call. |
| [2303109](../errorcode-net-socket.md#2303109-错误文件编号) | Bad file number. |
| [2303111](../errorcode-net-socket.md#2303111-资源暂时不可用请重试) | Resource temporarily unavailable. Try again. |
| [2303188](../errorcode-net-socket.md#2303188-非套接字的套接字操作) | Socket operation on non-socket. |
| [2303191](../errorcode-net-socket.md#2303191-socket协议类型错误) | Incorrect socket protocol type. |
| [2303198](../errorcode-net-socket.md#2303198-网络地址已被使用) | Address already in use. |
| [2303199](../errorcode-net-socket.md#2303199-不能分配请求的地址) | Cannot assign requested address. |
| [2303210](../errorcode-net-socket.md#2303210-连接超时) | Connection timed out. |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |
| [2303502](../errorcode-net-socket.md#2303502-tls读取错误) | An error occurred when reading data on the TLS socket. |
| [2303503](../errorcode-net-socket.md#2303503-tls写入错误) | An error occurred when writing data on the TLS socket. |
| [2303505](../errorcode-net-socket.md#2303505-tls系统调用错误) | An error occurred in the TLS system call. |
| [2303506](../errorcode-net-socket.md#2303506-关闭tls连接失败) | Failed to close the TLS connection. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2301206](../errorcode-net-socket.md#2301206-socks5连接代理服务器失败) | Socks5 failed to connect to the proxy server.<br>**适用版本：** 18+ |
| [2301207](../errorcode-net-socket.md#2301207-socks5认证用户名或密码无效) | Socks5 username or password is invalid.<br>**适用版本：** 18+ |
| [2301208](../errorcode-net-socket.md#2301208-socks5连接远程服务器失败) | Socks5 failed to connect to the remote server.<br>**适用版本：** 18+ |
| [2301209](../errorcode-net-socket.md#2301209-socks5协商认证方式失败) | Socks5 failed to negotiate the authentication method.<br>**适用版本：** 18+ |
| [2301210](../errorcode-net-socket.md#2301210-socks5发送消息失败) | Socks5 failed to send the message.<br>**适用版本：** 18+ |
| [2301211](../errorcode-net-socket.md#2301211-socks5接收消息失败) | Socks5 failed to receive the message.<br>**适用版本：** 18+ |
| [2301212](../errorcode-net-socket.md#2301212-socks5消息序列化失败) | Socks5 serialization error.<br>**适用版本：** 18+ |
| [2301213](../errorcode-net-socket.md#2301213-socks5消息反序列化失败) | Socks5 deserialization error.<br>**适用版本：** 18+ |

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

在TLSSocket上bind成功之后，进行通信连接，并创建和初始化TLS会话，实现建立连接过程，启动与服务器的TLS/SSL握手，实现数据传输功能，该连接包括两种认证方式，单向认证与双向认证，使用Promise异步回调。需要 注意options入参下secureOptions内的ca在API11及之前的版本为必填项，需填入服务端的ca证书(用于认证校验服务端的数字证书)，证书内容以"-----BEGIN CERTIFICATE-----"开头，以"-----END CERTIFICATE-----"结尾，自API12开始，为非必填项。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TLSConnectOptions](arkts-network-socket-tlsconnectoptions-i.md) | 是 | 连接所需要的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 以Promise形式返回，成功无返回，失败返回错误码，错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2303104](../errorcode-net-socket.md#2303104-中断系统调用) | Interrupted system call. |
| [2303109](../errorcode-net-socket.md#2303109-错误文件编号) | Bad file number. |
| [2303111](../errorcode-net-socket.md#2303111-资源暂时不可用请重试) | Resource temporarily unavailable. Try again. |
| [2303188](../errorcode-net-socket.md#2303188-非套接字的套接字操作) | Socket operation on non-socket. |
| [2303191](../errorcode-net-socket.md#2303191-socket协议类型错误) | Incorrect socket protocol type. |
| [2303198](../errorcode-net-socket.md#2303198-网络地址已被使用) | Address already in use. |
| [2303199](../errorcode-net-socket.md#2303199-不能分配请求的地址) | Cannot assign requested address. |
| [2303210](../errorcode-net-socket.md#2303210-连接超时) | Connection timed out. |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |
| [2303502](../errorcode-net-socket.md#2303502-tls读取错误) | An error occurred when reading data on the TLS socket. |
| [2303503](../errorcode-net-socket.md#2303503-tls写入错误) | An error occurred when writing data on the TLS socket. |
| [2303505](../errorcode-net-socket.md#2303505-tls系统调用错误) | An error occurred in the TLS system call. |
| [2303506](../errorcode-net-socket.md#2303506-关闭tls连接失败) | Failed to close the TLS connection. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2301206](../errorcode-net-socket.md#2301206-socks5连接代理服务器失败) | Socks5 failed to connect to the proxy server.<br>**适用版本：** 18+ |
| [2301207](../errorcode-net-socket.md#2301207-socks5认证用户名或密码无效) | Socks5 username or password is invalid.<br>**适用版本：** 18+ |
| [2301208](../errorcode-net-socket.md#2301208-socks5连接远程服务器失败) | Socks5 failed to connect to the remote server.<br>**适用版本：** 18+ |
| [2301209](../errorcode-net-socket.md#2301209-socks5协商认证方式失败) | Socks5 failed to negotiate the authentication method.<br>**适用版本：** 18+ |
| [2301210](../errorcode-net-socket.md#2301210-socks5发送消息失败) | Socks5 failed to send the message.<br>**适用版本：** 18+ |
| [2301211](../errorcode-net-socket.md#2301211-socks5接收消息失败) | Socks5 failed to receive the message.<br>**适用版本：** 18+ |
| [2301212](../errorcode-net-socket.md#2301212-socks5消息序列化失败) | Socks5 serialization error.<br>**适用版本：** 18+ |
| [2301213](../errorcode-net-socket.md#2301213-socks5消息反序列化失败) | Socks5 deserialization error.<br>**适用版本：** 18+ |

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

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[X509CertRawData](arkts-network-socket-x509certrawdata-t.md)&gt; | 是 | 回调函数，成功返回本地的证书，失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |
| [2303504](../errorcode-net-socket.md#2303504-查找x509时出错) | An error occurred when verifying the X.509 certificate. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
tls.getCertificate((err: BusinessError, data: socket.X509CertRawData) => {
  if (err) {
    console.error("getCertificate callback error = " + err);
  } else {
    console.info("getCertificate callback = " + data);
  }
});
```

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { util } from '@kit.ArkTS';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
tls.getCertificate().then((data: socket.X509CertRawData) => {
  const decoder = util.TextDecoder.create();
  const str = decoder.decodeToString(data.data);
  console.info("getCertificate: " + str);
}).catch((err: BusinessError) => {
  console.error("failed" + err);
});
```

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { util } from '@kit.ArkTS';

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
tlsServer.getCertificate((err: BusinessError, data: socket.X509CertRawData) => {
  if (err) {
    console.error("getCertificate callback error = " + err);
  } else {
    const decoder = util.TextDecoder.create();
    const str = decoder.decodeToString(data.data);
    console.info("getCertificate callback: " + str);
  }
});
```

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { util } from '@kit.ArkTS';

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
tlsServer.getCertificate().then((data: socket.X509CertRawData) => {
  const decoder = util.TextDecoder.create();
  const str = decoder.decodeToString(data.data);
  console.info("getCertificate: " + str);
}).catch((err: BusinessError) => {
  console.error("failed" + err);
});
```

## getCertificate

```TypeScript
getCertificate(): Promise<X509CertRawData>
```

在TLSSocket通信连接之后，获取本地的数字证书，该接口只适用于双向认证时，使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[X509CertRawData](arkts-network-socket-x509certrawdata-t.md)&gt; | 以Promise形式返回本地的数字证书的结果。失败返回错误码，错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |
| [2303504](../errorcode-net-socket.md#2303504-查找x509时出错) | An error occurred when verifying the X.509 certificate. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |

**示例**

参见 [getCertificate](#getcertificate)

## getCipherSuite

```TypeScript
getCipherSuite(callback: AsyncCallback<Array<string>>): void
```

在TLSSocket通信连接成功之后，获取通信双方协商后的加密套件，使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | 是 | 回调函数，返回通信双方支持的加密套件。失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |
| [2303502](../errorcode-net-socket.md#2303502-tls读取错误) | An error occurred when reading data on the TLS socket. |
| [2303505](../errorcode-net-socket.md#2303505-tls系统调用错误) | An error occurred in the TLS system call. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |

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
  console.error("failed" + err);
});
tlsServer.on('connect', (client: socket.TLSSocketConnection) => {
  client.getCipherSuite((err: BusinessError, data: Array<string>) => {
    if (err) {
      console.error("getCipherSuite callback error = " + err);
    } else {
      console.info("getCipherSuite callback = " + data);
    }
  });
});
```

## getCipherSuite

```TypeScript
getCipherSuite(): Promise<Array<string>>
```

在TLSSocket通信连接成功之后，获取通信双方协商后的加密套件，使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;Array & lt;string & gt; & gt; | 以Promise形式返回通信双方支持的加密套件。失败返回错误码，错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |
| [2303502](../errorcode-net-socket.md#2303502-tls读取错误) | An error occurred when reading data on the TLS socket. |
| [2303505](../errorcode-net-socket.md#2303505-tls系统调用错误) | An error occurred in the TLS system call. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |

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
  console.error("failed" + err);
});
tlsServer.on('connect', (client: socket.TLSSocketConnection) => {
  client.getCipherSuite().then((data: Array<string>) => {
    console.info('getCipherSuite success:' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
    console.error("failed" + err);
  });
});
```

## getLocalAddress

```TypeScript
getLocalAddress(): Promise<NetAddress>
```

获取TLSSocket的本地Socket地址。使用Promise异步回调。

> **说明：**
> 
> 在TLSSocketServer通信连接成功之后，才可调用此方法。

**起始版本：** 12

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;NetAddress & gt; | 以Promise形式返回获取本地socket地址的结果。 |

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

let udp: socket.UDPSocket = socket.constructUDPSocketInstance();

let bindAddr: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
udp.bind(bindAddr).then(() => {
  console.info('bind success');
  udp.getLocalAddress().then((localAddress: socket.NetAddress) => {
        console.info("UDP_Socket get SUCCESS! Address：" + JSON.stringify(localAddress));
      }).catch((err: BusinessError) => {
        console.error("UDP_Socket get FAILED! Error: " + JSON.stringify(err));
      })
}).catch((err: BusinessError) => {
  console.error('bind fail');
});
```

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

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcpServer: socket.TCPSocketServer = socket.constructTCPSocketServerInstance();
let listenAddr: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080,
  family: 1
}
tcpServer.listen(listenAddr).then(() => {
  tcpServer.getLocalAddress().then((localAddress: socket.NetAddress) => {
    console.info("SUCCESS! Address:" + JSON.stringify(localAddress));
  }).catch((err: BusinessError) => {
    console.error("FerrorAILED! Error:" + JSON.stringify(err));
  })
}).catch((err: BusinessError) => {
  console.error('listen fail');
});
```

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
  console.error("failed" + err);
});

tlsServer.on('connect', (client: socket.TLSSocketConnection) => {
  client.getLocalAddress().then((localAddress: socket.NetAddress) => {
    console.info("Family IP Port: " + JSON.stringify(localAddress));
  }).catch((err: BusinessError) => {
    console.error("TLS Client Get Family IP Port failed, error: " + JSON.stringify(err));
  })
});
```

## getProtocol

```TypeScript
getProtocol(callback: AsyncCallback<string>): void
```

在TLSSocket通信连接成功之后，获取通信的协议版本，使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数，返回通信的协议。失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |
| [2303505](../errorcode-net-socket.md#2303505-tls系统调用错误) | An error occurred in the TLS system call. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |

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

在TLSSocket通信连接成功之后，获取通信的协议版本，使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;string & gt; | 以Promise形式返回通信的协议。失败返回错误码，错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |
| [2303505](../errorcode-net-socket.md#2303505-tls系统调用错误) | An error occurred in the TLS system call. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |

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

## getRemoteAddress

```TypeScript
getRemoteAddress(callback: AsyncCallback<NetAddress>): void
```

在TLSSocket通信连接成功之后，获取对端Socket地址。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;NetAddress&gt; | 是 | 回调函数。成功返回对端的socket地址，失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2303188](../errorcode-net-socket.md#2303188-非套接字的套接字操作) | Socket operation on non-socket. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |

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
  console.error("failed" + err);
});
tlsServer.on('connect', (client: socket.TLSSocketConnection) => {
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

在TLSSocket通信连接成功之后，获取对端Socket地址。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;NetAddress & gt; | 以Promise形式返回获取对端socket地址的结果。失败返回错误码，错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2303188](../errorcode-net-socket.md#2303188-非套接字的套接字操作) | Socket operation on non-socket. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |

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
  console.error("failed" + err);
});
tlsServer.on('connect', (client: socket.TLSSocketConnection) => {
  client.getRemoteAddress().then((data: socket.NetAddress) => {
    console.info('getRemoteAddress success:' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
    console.error("failed" + err);
  });
});
```

## getRemoteCertificate

```TypeScript
getRemoteCertificate(callback: AsyncCallback<X509CertRawData>): void
```

在TLSSocket通信连接成功之后，获取服务端的数字证书，使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[X509CertRawData](arkts-network-socket-x509certrawdata-t.md)&gt; | 是 | 回调函数，返回服务端的证书。失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { util } from '@kit.ArkTS';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
tls.getRemoteCertificate((err: BusinessError, data: socket.X509CertRawData) => {
  if (err) {
    console.error("getRemoteCertificate callback error = " + err);
  } else {
    const decoder = util.TextDecoder.create();
    const str = decoder.decodeToString(data.data);
    console.info("getRemoteCertificate callback = " + str);
  }
});
```

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { util } from '@kit.ArkTS';

let tls: socket.TLSSocket = socket.constructTLSSocketInstance();
tls.getRemoteCertificate().then((data: socket.X509CertRawData) => {
  const decoder = util.TextDecoder.create();
  const str = decoder.decodeToString(data.data);
  console.info("getRemoteCertificate:" + str);
}).catch((err: BusinessError) => {
  console.error("failed" + err);
});
```

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { util } from '@kit.ArkTS';

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
  console.error("failed" + err);
});
tlsServer.on('connect', (client: socket.TLSSocketConnection) => {
  client.getRemoteCertificate((err: BusinessError, data: socket.X509CertRawData) => {
    if (err) {
      console.error("getRemoteCertificate callback error: " + err);
    } else {
      const decoder = util.TextDecoder.create();
      const str = decoder.decodeToString(data.data);
      console.info("getRemoteCertificate callback: " + str);
    }
  });
});
```

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { util } from '@kit.ArkTS';

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
  console.error("failed" + err);
});
tlsServer.on('connect', (client: socket.TLSSocketConnection) => {
  client.getRemoteCertificate().then((data: socket.X509CertRawData) => {
    const decoder = util.TextDecoder.create();
    const str = decoder.decodeToString(data.data);
    console.info("getRemoteCertificate success: " + str);
  }).catch((err: BusinessError) => {
    console.error("failed" + err);
  });
});
```

## getRemoteCertificate

```TypeScript
getRemoteCertificate(): Promise<X509CertRawData>
```

在TLSSocket通信连接成功之后，获取服务端的数字证书，使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[X509CertRawData](arkts-network-socket-x509certrawdata-t.md)&gt; | 以Promise形式返回服务端的数字证书的结果。失败返回错误码，错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |

**示例**

参见 [getRemoteCertificate](#getremotecertificate)

## getSignatureAlgorithms

```TypeScript
getSignatureAlgorithms(callback: AsyncCallback<Array<string>>): void
```

在TLSSocket通信连接成功之后，获取通信双方协商后签名算法，该接口只适配双向认证模式下，使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | 是 | 回调函数，返回双方支持的签名算法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |

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
  console.error("failed" + err);
});
tlsServer.on('connect', (client: socket.TLSSocketConnection) => {
  client.getSignatureAlgorithms((err: BusinessError, data: Array<string>) => {
    if (err) {
      console.error("getSignatureAlgorithms callback error = " + err);
    } else {
      console.info("getSignatureAlgorithms callback = " + data);
    }
  });
});
```

## getSignatureAlgorithms

```TypeScript
getSignatureAlgorithms(): Promise<Array<string>>
```

在TLSSocket通信连接成功之后，获取通信双方协商后的签名算法，该接口只适配双向认证模式下，使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;Array & lt;string & gt; & gt; | 以Promise形式返回获取到的双方支持的签名算法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |

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
  console.error("failed" + err);
});
tlsServer.on('connect', (client: socket.TLSSocketConnection) => {
  client.getSignatureAlgorithms().then((data: Array<string>) => {
    console.info("getSignatureAlgorithms success" + data);
  }).catch((err: BusinessError) => {
    console.error("failed" + err);
  });
});
```

## getSocketFd

```TypeScript
getSocketFd(): Promise<number>
```

获取TLSSocket的文件描述符。使用Promise异步回调。

> **说明：**
> 
> - bind方法调用成功后，才可调用此方法。
> 
> - 文件描述符的生命周期由系统管理，应用可以通过[close](#close)方法关闭Socket连接，避免直接操作
> 文件描述符进行关闭。

**起始版本：** 16

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | 以Promise形式返回socket的文件描述符。 |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let udp: socket.UDPSocket = socket.constructUDPSocketInstance();
let bindAddr: socket.NetAddress = {
    address: '192.168.xx.xxx',
    port: 8080
}
udp.bind(bindAddr)
  .then(() => {
    udp.getSocketFd()
      .then((fd: number) => {
        console.info(`Socket FD：${fd}`);
      }).catch((err: BusinessError) => {
      console.error(`getSocketFd fail: ${err.message}, errorCode: ${err.code}`);
    });
  }).catch((err: BusinessError) => {
  console.error('bind fail');
});
```

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

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcpServer: socket.TCPSocketServer = socket.constructTCPSocketServerInstance();
let listenAddr: socket.NetAddress = {
  address:  '192.168.xx.xxx',
  port: 8080,
  family: 1
}
tcpServer.listen(listenAddr).then(() => {
  console.info('listen success');
  tcpServer.getSocketFd().then((fd: number) => {
    console.info(`Socket FD：${fd}`);
  }).catch((err: BusinessError) => {
    console.error(`getSocketFd fail: ${err.message}, errorCode: ${err.code}`);
  });
}).catch((err: BusinessError) => {
  console.error('listen fail');
});
```

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

server.listen(listenAddr).then(() => {
  console.info("listen success");
  server.getSocketFd().then((fd: number) => {
    console.info(`Socket FD：${fd}`);
  }).catch((err: Object) => {
    console.error(`getSocketFd fail: ${JSON.stringify(err)}`);
  });
}).catch((err: Object) => {
  console.error("listen fail: " + JSON.stringify(err));
})
```

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
  tlsServer.on('connect', (client: socket.TLSSocketConnection) => {
    client.getSocketFd().then((fd: number) => {
      console.info(`Socket FD：${fd}`);
    }).catch((err: BusinessError) => {
      console.error(`getSocketFd fail: ${err.message}, errorCode: ${err.code}`);
    })
  });
}).catch((err: BusinessError) => {
  console.error(`listen failed: ${JSON.stringify(err)}`);
});
```

## getState

```TypeScript
getState(callback: AsyncCallback<SocketStateBase>): void
```

在TLSSocket的bind成功之后，获取TLSSocket状态。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SocketStateBase](arkts-network-socket-socketstatebase-i.md)&gt; | 是 | 回调函数。成功返回TLSSocket状态，失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2303188](../errorcode-net-socket.md#2303188-非套接字的套接字操作) | Socket operation on non-socket. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let udp: socket.UDPSocket = socket.constructUDPSocketInstance();
let bindAddr: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
udp.bind(bindAddr, (err: BusinessError) => {
  if (err) {
    console.error('bind fail');
    return;
  }
  console.error('bind success');
  udp.getState((err: BusinessError, data: socket.SocketStateBase) => {
    if (err) {
      console.error('getState fail');
      return;
    }
    console.info('getState success:' + JSON.stringify(data));
  })
})
```

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

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcpServer: socket.TCPSocketServer = socket.constructTCPSocketServerInstance();
let listenAddr: socket.NetAddress = {
  address:  '192.168.xx.xxx',
  port: 8080,
  family: 1
}
tcpServer.listen(listenAddr, (err: BusinessError) => {
  if (err) {
    console.error("listen fail");
    return;
  }
  console.info("listen success");
})
tcpServer.getState((err: BusinessError, data: socket.SocketStateBase) => {
  if (err) {
    console.error('getState fail');
    return;
  }
  console.info('getState success:' + JSON.stringify(data));
})
```

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

在TLSSocket的bind成功之后，获取TLSSocket状态。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[SocketStateBase](arkts-network-socket-socketstatebase-i.md)&gt; | 以Promise形式返回获取TLSSocket状态的结果。失败返回错误码，错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2303188](../errorcode-net-socket.md#2303188-非套接字的套接字操作) | Socket operation on non-socket. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let udp: socket.UDPSocket = socket.constructUDPSocketInstance();
let bindAddr: socket.NetAddress = {
  address: '192.168.xx.xxx',
  port: 8080
}
udp.bind(bindAddr, (err: BusinessError) => {
  if (err) {
    console.error('bind fail');
    return;
  }
  console.info('bind success');
  udp.getState().then((data: socket.SocketStateBase) => {
    console.info('getState success:' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
    console.error('getState fail' + JSON.stringify(err));
  });
});
```

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

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcpServer: socket.TCPSocketServer = socket.constructTCPSocketServerInstance();
let listenAddr: socket.NetAddress = {
  address:  '192.168.xx.xxx',
  port: 8080,
  family: 1
}
tcpServer.listen(listenAddr, (err: BusinessError) => {
  if (err) {
    console.error("listen fail");
    return;
  }
  console.info("listen success");
})
tcpServer.getState().then((data: socket.SocketStateBase) => {
  console.info('getState success' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error('getState fail');
});
```

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
})
server.getState().then((data: socket.SocketStateBase) => {
  console.info('getState success: ' + JSON.stringify(data));
}).catch((err: Object) => {
  console.error('getState fail: ' + JSON.stringify(err));
});
```

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

## off('message')

```TypeScript
off(type: 'message', callback?: Callback<SocketMessageInfo>): void
```

取消订阅TLSSocket连接的接收消息事件。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'message' | 是 | 订阅的事件类型。'message'：接收消息事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SocketMessageInfo](arkts-network-socket-socketmessageinfo-i.md)&gt; | 否 | 回调函数。TLSSocket连接取消订阅某类接受消息事件触发的调用函数，返回TLSSocket连接信息。<br>**起始版本：** 11 |

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

## off('connect' | 'close')

```TypeScript
off(type: 'connect' | 'close', callback?: Callback<void>): void
```

取消订阅TLSSocket的连接事件或关闭事件。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'connect' \| 'close' | 是 | 订阅的事件类型。   - 'connect'：连接事件。   - 'close'：关闭事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 否 | 回调函数。TLSSocket连接订阅某类事件触发的调用函数。 |

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

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'connect' \| 'close' | 是 | 订阅的事件类型。   - 'connect'：连接事件。   - 'close'：关闭事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 否 | 回调函数。TLSSocket连接订阅某类事件触发的调用函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

参见 off

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

取消订阅TLSSocket连接的error事件。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 订阅的事件类型。'error'：error事件。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 否 | 回调函数。TLSSocket连接取消订阅某类error事件触发的调用函数。 |

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

## on('message')

```TypeScript
on(type: 'message', callback: Callback<SocketMessageInfo>): void
```

订阅TLSSocket连接的接收消息事件。使用callback异步回调。

> **说明：**
> 
> bind方法调用成功后，才可调用此方法。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'message' | 是 | 订阅的事件类型。'message'：接收消息事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SocketMessageInfo](arkts-network-socket-socketmessageinfo-i.md)&gt; | 是 | 回调函数。TLSSocket连接订阅某类接受消息事件触发的调用函数，返回TLSSocket连接信息。<br>**起始版本：** 11 |

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

## on('connect' | 'close')

```TypeScript
on(type: 'connect' | 'close', callback: Callback<void>): void
```

订阅TLSSocket的连接事件或关闭事件。使用callback异步回调。

> **说明：**
> 
> bind方法调用成功后，才可调用此方法。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'connect' \| 'close' | 是 | 订阅的事件类型。   - 'connect'：连接事件。   - 'close'：关闭事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 回调函数。TLSSocket连接订阅某类事件触发的调用函数。 |

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

订阅TLSSocket的连接事件或关闭事件。使用callback异步回调。

> **说明：**
> 
> bind方法调用成功后，才可调用此方法。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'connect' \| 'close' | 是 | 订阅的事件类型。   - 'connect'：连接事件。   - 'close'：关闭事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 回调函数。TLSSocket连接订阅某类事件触发的调用函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

参见 on

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

订阅TLSSocket连接的error事件。使用callback异步回调。

> **说明：**
> 
> bind方法调用成功后，才可调用此方法。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 订阅的事件类型。'error'：error事件。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 是 | 回调函数。TLSSocket连接订阅某类error事件触发的调用函数。 |

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

## send

```TypeScript
send(data: string | ArrayBuffer, callback: AsyncCallback<void>): void
```

在TLSSocket通信连接成功之后，向服务端发送消息，使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string \| ArrayBuffer | 是 | 发送的数据内容。<br>**起始版本：** 9 - 11 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数,返回TLSSocket发送数据的结果。失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |
| [2303503](../errorcode-net-socket.md#2303503-tls写入错误) | An error occurred when writing data on the TLS socket. |
| [2303505](../errorcode-net-socket.md#2303505-tls系统调用错误) | An error occurred in the TLS system call. |
| [2303506](../errorcode-net-socket.md#2303506-关闭tls连接失败) | Failed to close the TLS connection. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |

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
  console.error("failed" + err);
});

tlsServer.on('connect', (client: socket.TLSSocketConnection) => {
  client.send('Hello, client!', (err: BusinessError) => {
    if (err) {
      console.error('send fail');
      return;
    }
    console.info('send success');
  });
});
```

## send

```TypeScript
send(data: string | ArrayBuffer): Promise<void>
```

在TLSSocket通信连接成功之后，向服务端发送消息，使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string \| ArrayBuffer | 是 | 发送的数据内容。<br>**起始版本：** 9 - 11 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 以Promise形式返回,返回TLSSocket发送数据的结果。失败返回错误码，错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |
| [2303503](../errorcode-net-socket.md#2303503-tls写入错误) | An error occurred when writing data on the TLS socket. |
| [2303505](../errorcode-net-socket.md#2303505-tls系统调用错误) | An error occurred in the TLS system call. |
| [2303506](../errorcode-net-socket.md#2303506-关闭tls连接失败) | Failed to close the TLS connection. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |

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
  console.error("failed" + err);
});

tlsServer.on('connect', (client: socket.TLSSocketConnection) => {
  client.send('Hello, client!').then(() => {
    console.info('send success');
  }).catch((err: BusinessError) => {
    console.error('send fail');
  });
});
```

## setExtraOptions

```TypeScript
setExtraOptions(options: TCPExtraOptions, callback: AsyncCallback<void>): void
```

在TLSSocket的bind成功之后，设置TCPSocket连接的其他属性。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TCPExtraOptions](arkts-network-socket-tcpextraoptions-i.md) | 是 | TCPSocket连接的其他属性，参考[TCPExtraOptions](arkts-network-socket-tcpextraoptions-i.md)。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。成功返回设置TCPSocket连接的其他属性的结果，失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2303188](../errorcode-net-socket.md#2303188-非套接字的套接字操作) | Socket operation on non-socket. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |

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

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcpServer: socket.TCPSocketServer = socket.constructTCPSocketServerInstance();
let listenAddr: socket.NetAddress = {
  address:  '192.168.xx.xxx',
  port: 8080,
  family: 1
}
tcpServer.listen(listenAddr, (err: BusinessError) => {
  if (err) {
    console.error("listen fail");
    return;
  }
  console.info("listen success");
})

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
tcpServer.setExtraOptions(tcpExtraOptions, (err: BusinessError) => {
  if (err) {
    console.error('setExtraOptions fail');
    return;
  }
  console.info('setExtraOptions success');
});
```

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

在TLSSocket的bind成功之后，设置TCPSocket连接的其他属性。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TCPExtraOptions](arkts-network-socket-tcpextraoptions-i.md) | 是 | TCPSocket连接的其他属性，参考[TCPExtraOptions](arkts-network-socket-tcpextraoptions-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2303188](../errorcode-net-socket.md#2303188-非套接字的套接字操作) | Socket operation on non-socket. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |

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

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tcpServer: socket.TCPSocketServer = socket.constructTCPSocketServerInstance();
let listenAddr: socket.NetAddress = {
  address:  '192.168.xx.xxx',
  port: 8080,
  family: 1
}

interface SocketLinger {
  on: boolean;
  linger: number;
}

tcpServer.listen(listenAddr, (err: BusinessError) => {
  if (err) {
    console.error("listen fail");
    return;
  }
  console.info("listen success");
})

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
tcpServer.setExtraOptions(tcpExtraOptions).then(() => {
  console.info('setExtraOptions success');
}).catch((err: BusinessError) => {
  console.error('setExtraOptions fail');
});
```

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
