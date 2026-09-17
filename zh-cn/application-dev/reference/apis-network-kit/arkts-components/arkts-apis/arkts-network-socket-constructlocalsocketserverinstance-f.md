# constructLocalSocketServerInstance

## 导入模块

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## constructLocalSocketServerInstance

```TypeScript
function constructLocalSocketServerInstance(): LocalSocketServer
```

创建一个LocalSocketServer对象。

**起始版本：** 11

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LocalSocketServer](arkts-network-socket-localsocketserver-i.md) | 返回一个LocalSocketServer对象。 |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
let server: socket.LocalSocketServer = socket.constructLocalSocketServerInstance();
```
