# ClientConnectionCloseCallback

```TypeScript
export type ClientConnectionCloseCallback = (clientConnection: WebSocketConnection, closeReason :CloseResult) => void
```

关闭WebSocketServer连接时，订阅close事件得到的指定客户端的关闭结果。

**起始版本：** 19

<!--Device-webSocket-export type ClientConnectionCloseCallback = (clientConnection: WebSocketConnection, closeReason :CloseResult) => void--><!--Device-webSocket-export type ClientConnectionCloseCallback = (clientConnection: WebSocketConnection, closeReason :CloseResult) => void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| clientConnection | [WebSocketConnection](arkts-network-websocket-websocketconnection-i.md) | 是 | 客户端信息，包括客户端的ip地址和端口号port。 |
| closeReason | [CloseResult](arkts-network-websocket-closeresult-i.md) | 是 | 关闭WebSocket连接时，订阅close事件得到的关闭结果。 |
