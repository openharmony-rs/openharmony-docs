# ProbeResultInfo

Defines the network probe result information.

**Since:** 26.0.0

**System capability:** SystemCapability.Communication.NetManager.Core

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## lossRate

```TypeScript
lossRate: number
```

Packet loss rate. The value range is [0, 100]. For example, 100 indicates 100% packet loss, and 50 indicates 50% packet loss.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core

## rtt

```TypeScript
rtt: number[]
```

Round-trip time (RTT), in milliseconds. Multiple probe packets are sent to the target host. The number of probe packets is determined by the **duration** parameter in the [queryProbeResult](arkts-network-connection-queryproberesult-f.md) API. The array elements are the minimum, average, maximum, and standard deviation of the RTTs of these probe packets, respectively.

**Type:** number[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core
