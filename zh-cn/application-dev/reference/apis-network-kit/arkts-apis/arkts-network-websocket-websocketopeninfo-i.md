# WebSocketOpenInfo

WebSocket连接成功后的详细信息。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
```

## message

```TypeScript
message: string
```

服务器返回的状态信息。与status字段对应，例如：status=101时，该字段返回"Switching Protocols"。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetStack

## protocol

```TypeScript
protocol?: string
```

服务器返回的协商后的协议。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetStack

## status

```TypeScript
status: number
```

服务器返回的状态码。例如：101表示建链成功并升级为websocket协议。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetStack
