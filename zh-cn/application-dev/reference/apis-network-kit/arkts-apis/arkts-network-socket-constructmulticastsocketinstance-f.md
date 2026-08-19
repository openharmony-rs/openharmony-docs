# constructMulticastSocketInstance

## 导入模块

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## constructMulticastSocketInstance

```TypeScript
function constructMulticastSocketInstance(): MulticastSocket
```

创建一个MulticastSocket对象。

**起始版本：** 11

<!--Device-socket-function constructMulticastSocketInstance(): MulticastSocket--><!--Device-socket-function constructMulticastSocketInstance(): MulticastSocket-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MulticastSocket](arkts-network-socket-multicastsocket-i.md) | 返回一个MulticastSocket对象。 |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
let multicast: socket.MulticastSocket = socket.constructMulticastSocketInstance();
```

