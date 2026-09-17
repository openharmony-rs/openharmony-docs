# ClientConnectionCloseCallback

```TypeScript
export type ClientConnectionCloseCallback = (clientConnection: WebSocketConnection, closeReason :CloseResult) => void
```

Callback invoked when the WebSocketServer connection is closed.

**Since:** 19

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| clientConnection | [WebSocketConnection](arkts-network-websocket-websocketconnection-i.md) | Yes | the connection which is closed. |
| closeReason | [CloseResult](arkts-network-websocket-closeresult-i.md) | Yes | the error code and reason why the connection is closed. |
