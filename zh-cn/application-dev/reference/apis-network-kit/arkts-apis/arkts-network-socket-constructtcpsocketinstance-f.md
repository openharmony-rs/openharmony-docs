# constructTCPSocketInstance

## 导入模块

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## constructTCPSocketInstance

```TypeScript
function constructTCPSocketInstance(): TCPSocket
```

创建一个TCPSocket对象。

**起始版本：** 7

<!--Device-socket-function constructTCPSocketInstance(): TCPSocket--><!--Device-socket-function constructTCPSocketInstance(): TCPSocket-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| TCPSocket | 返回一个TCPSocket对象。 |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
```

