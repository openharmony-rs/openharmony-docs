# WebSocketCloseOptions

关闭WebSocket连接时，可选参数的类型和说明。

**起始版本：** 23

<!--Device-webSocket-export interface WebSocketCloseOptions--><!--Device-webSocket-export interface WebSocketCloseOptions-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { webSocket } from '@kit.NetworkKit';
```

## code

```TypeScript
code?: int
```

错误码，关闭WebSocket连接时的可选参数，可根据实际情况来填。传入值必须为正整数，取值范围为[1000,1015]。如果未指定错误码或传入值不在上述范围内，code将会被设置为默认值1000。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebSocketCloseOptions-code?: int--><!--Device-WebSocketCloseOptions-code?: int-End-->

**系统能力：** SystemCapability.Communication.NetStack

## reason

```TypeScript
reason?: string
```

原因值，关闭WebSocket连接时的可选参数，可根据实际情况来填。如果未指定原因值，则原因值将会被设置为默认值"CLOSE_NORMAL"。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebSocketCloseOptions-reason?: string--><!--Device-WebSocketCloseOptions-reason?: string-End-->

**系统能力：** SystemCapability.Communication.NetStack

