# createWebSocketServer

## 导入模块

```TypeScript
import { webSocket } from '@kit.NetworkKit';
```

## createWebSocketServer

```TypeScript
function createWebSocketServer(): WebSocketServer
```

创建一个WebSocketServer对象，包括启动服务、发送数据、关闭连接、列出客户端信息、停止服务，订阅/取消订阅webSocket连接的连接事件、接收到客户端消息事件、关闭事件和错误事件。 > **说明：** > > 从API version 23开始支持全设备使用，之前仅支持TV设备使用。

**起始版本：** 23

<!--Device-webSocket-function createWebSocketServer(): WebSocketServer--><!--Device-webSocket-function createWebSocketServer(): WebSocketServer-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WebSocketServer](arkts-network-websocket-websocketserver-i.md) | 返回一个WebSocketServer对象，里面包括start、listAllConnections、send、close、stop、on和off方法。 |

**示例**

```TypeScript
let ws: webSocket.WebSocketServer = webSocket.createWebSocketServer();
```

