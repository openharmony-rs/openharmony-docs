# constructTCPSocketInstance

## Modules to Import

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## constructTCPSocketInstance

```TypeScript
function constructTCPSocketInstance(): TCPSocket
```

Creates a **TCPSocket** object.

**Since:** 7

**System capability:** SystemCapability.Communication.NetStack

**Return value:**

| Type | Description |
| --- | --- |
| [TCPSocket](arkts-network-socket-tcpsocket-i.md) | **TCPSocket** object. |

**Examples**

```TypeScript
import { socket } from '@kit.NetworkKit';
let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
```
