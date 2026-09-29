# TraceRouteInfo

```TypeScript
export interface TraceRouteInfo
```

Defines the route tracing information.

**Since:** 26.0.0

<!--Device-connection-export interface TraceRouteInfo--><!--Device-connection-export interface TraceRouteInfo-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## address

```TypeScript
address: string
```

IP address to jump to.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-TraceRouteInfo-address: string--><!--Device-TraceRouteInfo-address: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## jumpNo

```TypeScript
jumpNo: number
```

Jump number.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-TraceRouteInfo-jumpNo: int--><!--Device-TraceRouteInfo-jumpNo: int-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## rtt

```TypeScript
rtt: number[]
```

Round-trip time (RTT), in milliseconds. Five probe packets are sent for each jump. The array elements are the minimum, average, maximum, and standard deviation of the RTTs of these probe packets, respectively.

**Type:** number[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-TraceRouteInfo-rtt: int[]--><!--Device-TraceRouteInfo-rtt: int[]-End-->

**System capability:** SystemCapability.Communication.NetManager.Core
