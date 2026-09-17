# constructTCPSocketServerInstance

## 导入模块

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## constructTCPSocketServerInstance

```TypeScript
function constructTCPSocketServerInstance(): TCPSocketServer
```

创建一个TCPSocketServer对象。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TCPSocketServer](arkts-network-socket-tcpsocketserver-i.md) | 返回一个TCPSocketServer对象。 |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
let tcpServer: socket.TCPSocketServer = socket.constructTCPSocketServerInstance();
```
