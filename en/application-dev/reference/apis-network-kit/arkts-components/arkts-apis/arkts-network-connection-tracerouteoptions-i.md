# TraceRouteOptions

```TypeScript
export interface TraceRouteOptions
```

Defines options for route tracing.

**Since:** 26.0.0

<!--Device-connection-export interface TraceRouteOptions--><!--Device-connection-export interface TraceRouteOptions-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## maxJumpNumber

```TypeScript
maxJumpNumber?: number
```

Maximum number of jumps. The value range is [1, 30]. The default value is **30**.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-TraceRouteOptions-maxJumpNumber?: int--><!--Device-TraceRouteOptions-maxJumpNumber?: int-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## packetsType

```TypeScript
packetsType?: PacketsType
```

Type of the data packet used for probe. The default value is **NETCONN_PACKETS_ICMP**.

**Type:** [PacketsType](arkts-network-connection-packetstype-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-TraceRouteOptions-packetsType?: PacketsType--><!--Device-TraceRouteOptions-packetsType?: PacketsType-End-->

**System capability:** SystemCapability.Communication.NetManager.Core
