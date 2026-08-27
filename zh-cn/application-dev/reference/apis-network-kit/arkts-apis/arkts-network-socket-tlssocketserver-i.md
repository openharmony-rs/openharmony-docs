# TLSSocketServer

TLSSocketServer连接。在调用TLSSocketServer的方法前，需要先通过 [socket.constructTLSSocketServerInstance](arkts-network-socket-constructtlssocketserverinstance-f.md)创建TLSSocketServer对象。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## close

```TypeScript
close(): Promise<void>
```

TLSSocketServer停止监听并释放通过[listen](arkts-network-socket-tcpsocketserver-i.md#listen)方法绑定的端口。使用Promise异步回调。

> **说明：**
> 
> 该方法不会关闭已有连接。如需关闭，请调用[TLSSocketConnection](arkts-network-socket-tlssocketconnection-i.md)的
> [close](arkts-network-socket-tcpsocketconnection-i.md#close)方法。

**起始版本：** 20

**需要权限：** ohos.permission.INTERNET

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
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

## getCertificate

```TypeScript
getCertificate(callback: AsyncCallback<X509CertRawData>): void
```

在TLSSocketServer通信连接成功之后，获取本地的数字证书，使用callback异步回调。

> **说明：**
> 
> listen方法调用成功后，才可调用此方法。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[X509CertRawData](arkts-network-socket-x509certrawdata-t.md)&gt; | 是 | 回调函数，成功返回本地的证书，失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
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

在TLSSocketServer通信连接之后，获取本地的数字证书，使用Promise异步回调。

> **说明：**
> 
> listen方法调用成功后，才可调用此方法。

**起始版本：** 10

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

## getLocalAddress

```TypeScript
getLocalAddress(): Promise<NetAddress>
```

获取TLSSocketServer的本地Socket地址。使用Promise异步回调。

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

在TLSSocketServer通信连接成功之后，获取通信的协议版本，使用callback异步回调。

> **说明：**
> 
> listen方法调用成功后，才可调用此方法。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数，返回通信的协议。失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
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

在TLSSocketServer通信连接成功之后，获取通信的协议版本，使用Promise异步回调。

> **说明：**
> 
> listen方法调用成功后，才可调用此方法。

**起始版本：** 10

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

## getSocketFd

```TypeScript
getSocketFd(): Promise<number>
```

获取TLSSocketServer监听端口绑定的文件描述符。使用Promise异步回调。

> **说明：**
> 
> - [listen](arkts-network-socket-tcpsocketserver-i.md#listen)方法调用成功后，才可调用此方法。多次调用listen时，会获取最新监听端口绑定的文件描述符。
> 
> - 监听异常、Socket已关闭（如调用close后）等异常情况下调用本接口会返回-1。
> 
> - 文件描述符的生命周期由系统管理，应用可以通过[close](arkts-network-socket-tcpsocketserver-i.md#close)方法关闭Socket连接，避免直接操作文件描述符进行关闭。

**起始版本：** 23

**需要权限：** ohos.permission.INTERNET

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | Promise对象，返回Socket的文件描述符。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

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

在TLSSocketServer的listen成功之后，获取TLSSocketServer状态。使用callback异步回调。

> **说明：**
> 
> listen方法调用成功后，才可调用此方法。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SocketStateBase](arkts-network-socket-socketstatebase-i.md)&gt; | 是 | 回调函数。成功返回TLSSocketServer状态，失败返回错误码、错误信息。 |

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

在TLSSocketServer的listen成功之后，获取TLSSocketServer状态。使用Promise异步回调。

> **说明：**
> 
> listen方法调用成功后，才可调用此方法。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[SocketStateBase](arkts-network-socket-socketstatebase-i.md)&gt; | 以Promise形式返回获取TLSSocketServer状态的结果。失败返回错误码，错误信息。 |

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

## listen

```TypeScript
listen(options: TLSConnectOptions, callback: AsyncCallback<void>): void
```

绑定IP地址和端口，在TLSSocketServer上bind成功之后，监听客户端的连接，创建和初始化TLS会话，实现建立连接过程，加载证书秘钥并验证，使用callback异步回调。

> **注意：**
> 
> IP地址设置为0.0.0.0时，可以监听本机所有地址。

**起始版本：** 10

**需要权限：** ohos.permission.INTERNET

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TLSConnectOptions](arkts-network-socket-tlsconnectoptions-i.md) | 是 | TLSSocketServer连接所需要的参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，成功返回空，失败返回错误码、错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2303109](../errorcode-net-socket.md#2303109-错误文件编号) | Bad file number. |
| [2303111](../errorcode-net-socket.md#2303111-资源暂时不可用请重试) | Resource temporarily unavailable. Try again. |
| [2303198](../errorcode-net-socket.md#2303198-网络地址已被使用) | Address already in use. |
| [2303199](../errorcode-net-socket.md#2303199-不能分配请求的地址) | Cannot assign requested address. |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |
| [2303502](../errorcode-net-socket.md#2303502-tls读取错误) | An error occurred when reading data on the TLS socket. |
| [2303503](../errorcode-net-socket.md#2303503-tls写入错误) | An error occurred when writing data on the TLS socket. |
| [2303505](../errorcode-net-socket.md#2303505-tls系统调用错误) | An error occurred in the TLS system call. |
| [2303506](../errorcode-net-socket.md#2303506-关闭tls连接失败) | Failed to close the TLS connection. |

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

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TLSConnectOptions](arkts-network-socket-tlsconnectoptions-i.md) | 是 | 连接所需要的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 以Promise形式返回，成功返回空，失败返回错误码，错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2300002](../errorcode-net-socket.md#2300002-系统内部错误) | System internal error. |
| [2303109](../errorcode-net-socket.md#2303109-错误文件编号) | Bad file number. |
| [2303111](../errorcode-net-socket.md#2303111-资源暂时不可用请重试) | Resource temporarily unavailable. Try again. |
| [2303198](../errorcode-net-socket.md#2303198-网络地址已被使用) | Address already in use. |
| [2303199](../errorcode-net-socket.md#2303199-不能分配请求的地址) | Cannot assign requested address. |
| [2303501](../errorcode-net-socket.md#2303501-ssl为空) | SSL is null. |
| [2303502](../errorcode-net-socket.md#2303502-tls读取错误) | An error occurred when reading data on the TLS socket. |
| [2303503](../errorcode-net-socket.md#2303503-tls写入错误) | An error occurred when writing data on the TLS socket. |
| [2303505](../errorcode-net-socket.md#2303505-tls系统调用错误) | An error occurred in the TLS system call. |
| [2303506](../errorcode-net-socket.md#2303506-关闭tls连接失败) | Failed to close the TLS connection. |

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

取消订阅TLSSocketServer的连接事件。使用callback异步回调。

> **说明：**
> 
> listen方法调用成功后，才可调用此方法。
> 
> 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'connect' | 是 | 订阅的事件类型。'connect'：连接事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[TLSSocketConnection](arkts-network-socket-tlssocketconnection-i.md)&gt; | 否 | 回调函数。失败时返回错误码、错误信息。 |

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

取消订阅TLSSocketServer连接的error事件。使用callback异步回调。

> **说明：**
> 
> listen方法调用成功后，才可调用此方法。
> 
> 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 订阅的事件类型。'error'：error事件。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 否 | 回调函数。失败时返回错误码、错误信息。 |

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

订阅TLSSocketServer的连接事件。使用callback异步回调。

> **说明：**
> 
> listen方法调用成功后，才可调用此方法。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'connect' | 是 | 订阅的事件类型。'connect'：连接事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[TLSSocketConnection](arkts-network-socket-tlssocketconnection-i.md)&gt; | 是 | 回调函数。失败时返回错误码、错误信息。 |

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

订阅TLSSocketServer连接的error事件。使用callback异步回调。

> **说明：**
> 
> listen方法调用成功后，才可调用此方法。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 订阅的事件类型。'error'：error事件。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 是 | 回调函数。失败时返回错误码、错误信息。 |

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

在TLSSocketServer的listen成功之后，设置TLSSocketServer连接的其他属性。使用callback异步回调。

> **说明：**
> 
> listen方法调用成功后，才可调用此方法。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TCPExtraOptions](arkts-network-socket-tcpextraoptions-i.md) | 是 | TLSSocketServer连接的其他属性。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。成功返回空，失败返回错误码、错误信息。 |

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

在TLSSocketServer的listen成功之后，设置TLSSocketServer连接的其他属性，使用Promise异步回调。

> **说明：**
> 
> listen方法调用成功后，才可调用此方法。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TCPExtraOptions](arkts-network-socket-tcpextraoptions-i.md) | 是 | TLSSocketServer连接的其他属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 以Promise形式返回，成功返回空，失败返回错误码，错误信息。 |

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
