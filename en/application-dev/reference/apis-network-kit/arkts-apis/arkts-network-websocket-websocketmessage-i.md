# WebSocketMessage

```TypeScript
export interface WebSocketMessage
```

Callback used to return the result, which contains:

**Since:** 19

<!--Device-webSocket-export interface WebSocketMessage--><!--Device-webSocket-export interface WebSocketMessage-End-->

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { webSocket } from '@kit.NetworkKit';
```

## clientConnection

```TypeScript
clientConnection: WebSocketConnection
```

Client information, including the IP address and port number.

**Type:** [WebSocketConnection](arkts-network-websocket-websocketconnection-i.md)

**Since:** 19

<!--Device-WebSocketMessage-clientConnection: WebSocketConnection--><!--Device-WebSocketMessage-clientConnection: WebSocketConnection-End-->

**System capability:** SystemCapability.Communication.NetStack

## data

```TypeScript
data: string | ArrayBuffer
```

Message data sent by the client.

**Type:** string &#124; ArrayBuffer

**Since:** 19

<!--Device-WebSocketMessage-data: string | ArrayBuffer--><!--Device-WebSocketMessage-data: string | ArrayBuffer-End-->

**System capability:** SystemCapability.Communication.NetStack
