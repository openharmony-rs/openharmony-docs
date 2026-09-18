# constructLocalSocketInstance

## 导入模块

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## constructLocalSocketInstance

```TypeScript
function constructLocalSocketInstance(): LocalSocket
```

创建一个LocalSocket对象。

**起始版本：** 11

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LocalSocket](arkts-network-socket-localsocket-i.md) | 返回一个LocalSocket对象。 |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
let client: socket.LocalSocket = socket.constructLocalSocketInstance();
```
