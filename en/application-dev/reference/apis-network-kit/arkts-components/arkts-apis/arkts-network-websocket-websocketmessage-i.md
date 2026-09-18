# WebSocketMessage

Callback used to return the result, which contains:

**Since:** 19

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

**System capability:** SystemCapability.Communication.NetStack

## data

```TypeScript
data: string | ArrayBuffer
```

Message data sent by the client.

**Type:** string &#124; ArrayBuffer

**Since:** 19

**System capability:** SystemCapability.Communication.NetStack
