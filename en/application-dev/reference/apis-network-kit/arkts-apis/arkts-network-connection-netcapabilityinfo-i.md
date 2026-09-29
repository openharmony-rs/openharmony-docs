# NetCapabilityInfo

```TypeScript
export interface NetCapabilityInfo
```

Provides an instance that bears data network capabilities.

**Since:** 10

<!--Device-connection-export interface NetCapabilityInfo--><!--Device-connection-export interface NetCapabilityInfo-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## netCap

```TypeScript
netCap: NetCapabilities
```

Network transmission capabilities and bearer types of the data network.

**Type:** [NetCapabilities](arkts-network-connection-netcapabilities-i.md)

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-NetCapabilityInfo-netCap: NetCapabilities--><!--Device-NetCapabilityInfo-netCap: NetCapabilities-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## netHandle

```TypeScript
netHandle: NetHandle
```

Network handle.

**Type:** [NetHandle](arkts-network-connection-nethandle-i.md)

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-NetCapabilityInfo-netHandle: NetHandle--><!--Device-NetCapabilityInfo-netHandle: NetHandle-End-->

**System capability:** SystemCapability.Communication.NetManager.Core
