# CloseResult

关闭WebSocket连接时，订阅close事件得到的关闭结果。

**起始版本：** 23

<!--Device-webSocket-export interface CloseResult--><!--Device-webSocket-export interface CloseResult-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { webSocket } from '@kit.NetworkKit';
```

## code

```TypeScript
code: int
```

错误码，订阅close事件得到的关闭连接的错误码。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CloseResult-code: int--><!--Device-CloseResult-code: int-End-->

**系统能力：** SystemCapability.Communication.NetStack

## reason

```TypeScript
reason: string
```

原因值，订阅close事件得到的关闭连接的错误原因。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CloseResult-reason: string--><!--Device-CloseResult-reason: string-End-->

**系统能力：** SystemCapability.Communication.NetStack

