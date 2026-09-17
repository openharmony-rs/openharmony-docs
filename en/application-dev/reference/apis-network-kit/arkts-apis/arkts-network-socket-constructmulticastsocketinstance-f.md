# constructMulticastSocketInstance

## Modules to Import

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## constructMulticastSocketInstance

```TypeScript
function constructMulticastSocketInstance(): MulticastSocket
```

Creates a **MulticastSocket** object.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Return value:**

| Type | Description |
| --- | --- |
| [MulticastSocket](arkts-network-socket-multicastsocket-i.md) | **MulticastSocket** object. |

**Examples**

```TypeScript
import { socket } from '@kit.NetworkKit';
let multicast: socket.MulticastSocket = socket.constructMulticastSocketInstance();
```
