# constructTLSSocketServerInstance

## 导入模块

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## constructTLSSocketServerInstance

```TypeScript
function constructTLSSocketServerInstance(): TLSSocketServer
```

创建并返回一个TLSSocketServer对象。

**起始版本：** 10

<!--Device-socket-function constructTLSSocketServerInstance(): TLSSocketServer--><!--Device-socket-function constructTLSSocketServerInstance(): TLSSocketServer-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TLSSocketServer](arkts-network-socket-tlssocketserver-i.md) | 返回一个TLSSocketServer对象。 |

**示例**

```TypeScript
import { socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tlsServer: socket.TLSSocketServer = socket.constructTLSSocketServerInstance();
```

