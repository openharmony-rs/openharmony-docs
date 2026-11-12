# ClientConnectionCloseCallback

```TypeScript
export type ClientConnectionCloseCallback = (clientConnection: WebSocketConnection, closeReason :CloseResult) => void
```

Callback invoked when the WebSocketServer connection is closed.

**Since:** 19

<!--Device-webSocket-export type ClientConnectionCloseCallback = (clientConnection: WebSocketConnection, closeReason :CloseResult) => void--><!--Device-webSocket-export type ClientConnectionCloseCallback = (clientConnection: WebSocketConnection, closeReason :CloseResult) => void-End-->

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| clientConnection | [WebSocketConnection](arkts-network-websocket-websocketconnection-i.md) | Yes | Client information, including the IP address and port number. |
| closeReason | [CloseResult](arkts-network-websocket-closeresult-i.md) | Yes | Represents the result obtained from the close event reported when the WebSocket connection is closed. |
