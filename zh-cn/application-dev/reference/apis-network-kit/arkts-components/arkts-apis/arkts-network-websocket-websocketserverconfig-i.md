# WebSocketServerConfig

```TypeScript
export interface WebSocketServerConfig
```

启动服务端的service时，需要输入的配置信息和说明。

**起始版本：** 19

<!--Device-webSocket-export interface WebSocketServerConfig--><!--Device-webSocket-export interface WebSocketServerConfig-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { webSocket } from '@kit.NetworkKit';
```

## maxConcurrentClientsNumber

```TypeScript
maxConcurrentClientsNumber: number
```

最大并发客户端数量，当达到最大数时，服务端拒绝新连接。默认最大数量为10。

**类型：** number

**起始版本：** 19

<!--Device-WebSocketServerConfig-maxConcurrentClientsNumber: int--><!--Device-WebSocketServerConfig-maxConcurrentClientsNumber: int-End-->

**系统能力：** SystemCapability.Communication.NetStack

## maxConnectionsForOneClient

```TypeScript
maxConnectionsForOneClient: number
```

单个客户端的最大连接数。默认最大数量为10。

**类型：** number

**起始版本：** 19

<!--Device-WebSocketServerConfig-maxConnectionsForOneClient: int--><!--Device-WebSocketServerConfig-maxConnectionsForOneClient: int-End-->

**系统能力：** SystemCapability.Communication.NetStack

## protocol

```TypeScript
protocol?: string
```

自定义协议。

**类型：** string

**起始版本：** 19

<!--Device-WebSocketServerConfig-protocol?: string--><!--Device-WebSocketServerConfig-protocol?: string-End-->

**系统能力：** SystemCapability.Communication.NetStack

## serverCert

```TypeScript
serverCert?: ServerCert
```

指定服务端证书的信息，包括服务端证书文件路径和服务端证书的私钥文件路径。

**类型：** [ServerCert](arkts-network-websocket-servercert-i.md)

**起始版本：** 19

<!--Device-WebSocketServerConfig-serverCert?: ServerCert--><!--Device-WebSocketServerConfig-serverCert?: ServerCert-End-->

**系统能力：** SystemCapability.Communication.NetStack

## serverIP

```TypeScript
serverIP?: string
```

服务端监听特定ip地址，默认是"0.0.0.0"。

**类型：** string

**起始版本：** 19

<!--Device-WebSocketServerConfig-serverIP?: string--><!--Device-WebSocketServerConfig-serverIP?: string-End-->

**系统能力：** SystemCapability.Communication.NetStack

## serverPort

```TypeScript
serverPort: number
```

服务端监听的端口号。

**类型：** number

**起始版本：** 19

<!--Device-WebSocketServerConfig-serverPort: int--><!--Device-WebSocketServerConfig-serverPort: int-End-->

**系统能力：** SystemCapability.Communication.NetStack
