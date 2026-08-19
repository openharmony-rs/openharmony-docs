# WebSocketMessage

从指定客户端接收到的消息，包括客户端的信息和数据。

**起始版本：** 23

<!--Device-webSocket-export interface WebSocketMessage--><!--Device-webSocket-export interface WebSocketMessage-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { webSocket } from '@kit.NetworkKit';
```

## clientConnection

```TypeScript
clientConnection: WebSocketConnection
```

客户端信息，包括客户端的ip地址和端口号port。

**类型：** [WebSocketConnection](arkts-network-websocket-websocketconnection-i.md)

**起始版本：** 23

<!--Device-WebSocketMessage-clientConnection: WebSocketConnection--><!--Device-WebSocketMessage-clientConnection: WebSocketConnection-End-->

**系统能力：** SystemCapability.Communication.NetStack

## data

```TypeScript
data: string | ArrayBuffer
```

接收到的客户端发的消息数据。

**类型：** string \| ArrayBuffer

**起始版本：** 23

<!--Device-WebSocketMessage-data: string | ArrayBuffer--><!--Device-WebSocketMessage-data: string | ArrayBuffer-End-->

**系统能力：** SystemCapability.Communication.NetStack

