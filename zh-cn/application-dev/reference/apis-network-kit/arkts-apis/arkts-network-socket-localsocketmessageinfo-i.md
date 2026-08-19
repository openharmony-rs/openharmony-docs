# LocalSocketMessageInfo

LocalSocket客户端与服务端通信时接收的数据。

**起始版本：** 11

<!--Device-socket-export interface LocalSocketMessageInfo--><!--Device-socket-export interface LocalSocketMessageInfo-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## address

```TypeScript
address: string
```

使用的本地套接字路径。

**类型：** string

**起始版本：** 11

<!--Device-LocalSocketMessageInfo-address: string--><!--Device-LocalSocketMessageInfo-address: string-End-->

**系统能力：** SystemCapability.Communication.NetStack

## message

```TypeScript
message: ArrayBuffer
```

收到的消息数据。

**类型：** ArrayBuffer

**起始版本：** 11

<!--Device-LocalSocketMessageInfo-message: ArrayBuffer--><!--Device-LocalSocketMessageInfo-message: ArrayBuffer-End-->

**系统能力：** SystemCapability.Communication.NetStack

## size

```TypeScript
size: int
```

数据长度。

**类型：** int

**起始版本：** 11

<!--Device-LocalSocketMessageInfo-size: int--><!--Device-LocalSocketMessageInfo-size: int-End-->

**系统能力：** SystemCapability.Communication.NetStack

