# createWebSocket

## Modules to Import

```TypeScript
import { webSocket } from '@kit.NetworkKit';
```

## createWebSocket

```TypeScript
function createWebSocket(): WebSocket
```

Creates a **WebSocket** object, which provides methods to create or close a WebSocket connection, send data over the connection, and enable or disable listening for the **open**, **close**, **message**, and **error** events.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

**Return value:**

| Type | Description |
| --- | --- |
| [WebSocket](arkts-network-websocket-websocket-i.md) | A **WebSocket** object, which contains the **connect**, **send**, **close**, **on**, or **off** method. |

**Examples**

```TypeScript
let ws: webSocket.WebSocket = webSocket.createWebSocket();
```
