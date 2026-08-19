# createWebSocket

## 导入模块

```TypeScript
import { webSocket } from '@kit.NetworkKit';
```

## createWebSocket

```TypeScript
function createWebSocket(): WebSocket
```

创建一个WebSocket对象，里面包括建立连接、关闭连接、发送数据和订阅/取消订阅WebSocket连接的打开事件、接收到服务器消息事件、关闭事件和错误事件。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-webSocket-function createWebSocket(): WebSocket--><!--Device-webSocket-function createWebSocket(): WebSocket-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WebSocket](arkts-network-websocket-websocket-i.md) | 返回一个WebSocket对象，里面包括connect、send、close、on和off方法。 |

**示例**

```TypeScript
let ws: webSocket.WebSocket = webSocket.createWebSocket();
```

