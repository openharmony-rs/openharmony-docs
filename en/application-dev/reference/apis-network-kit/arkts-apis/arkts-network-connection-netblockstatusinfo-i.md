# NetBlockStatusInfo

Obtains the network block status information.

**Since:** 11

**System capability:** SystemCapability.Communication.NetManager.Core

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## blocked

```TypeScript
blocked: boolean
```

Whether the current network is blocked. The value **true** indicates that the network is congested, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 11

**System capability:** SystemCapability.Communication.NetManager.Core

## netHandle

```TypeScript
netHandle: NetHandle
```

Network handle.

**Type:** [NetHandle](arkts-network-connection-nethandle-i.md)

**Since:** 11

**System capability:** SystemCapability.Communication.NetManager.Core
