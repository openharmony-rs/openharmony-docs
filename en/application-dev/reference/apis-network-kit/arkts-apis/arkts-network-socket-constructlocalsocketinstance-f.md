# constructLocalSocketInstance

## Modules to Import

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## constructLocalSocketInstance

```TypeScript
function constructLocalSocketInstance(): LocalSocket
```

Creates a **LocalSocket** object.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Return value:**

| Type | Description |
| --- | --- |
| [LocalSocket](arkts-network-socket-localsocket-i.md) | **LocalSocket** object. |

**Examples**

```TypeScript
import { socket } from '@kit.NetworkKit';
let client: socket.LocalSocket = socket.constructLocalSocketInstance();
```
