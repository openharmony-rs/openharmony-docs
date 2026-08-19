# WebSocketOpenInfo

WebSocket连接成功后的详细信息。

**起始版本：** 26.0.0

<!--Device-webSocket-export interface WebSocketOpenInfo--><!--Device-webSocket-export interface WebSocketOpenInfo-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { webSocket } from '@kit.NetworkKit';
```

## message

```TypeScript
message: string
```

服务器返回的状态信息。与status字段对应，例如：status=101时，该字段返回"Switching Protocols"。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebSocketOpenInfo-message: string--><!--Device-WebSocketOpenInfo-message: string-End-->

**系统能力：** SystemCapability.Communication.NetStack

## protocol

```TypeScript
protocol?: string
```

服务器返回的协商后的协议。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebSocketOpenInfo-protocol?: string--><!--Device-WebSocketOpenInfo-protocol?: string-End-->

**系统能力：** SystemCapability.Communication.NetStack

## status

```TypeScript
status: int
```

服务器返回的状态码。例如：101表示建链成功并升级为websocket协议。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebSocketOpenInfo-status: int--><!--Device-WebSocketOpenInfo-status: int-End-->

**系统能力：** SystemCapability.Communication.NetStack

