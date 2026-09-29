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

<!--Device-socket-function constructMulticastSocketInstance(): MulticastSocket--><!--Device-socket-function constructMulticastSocketInstance(): MulticastSocket-End-->

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
