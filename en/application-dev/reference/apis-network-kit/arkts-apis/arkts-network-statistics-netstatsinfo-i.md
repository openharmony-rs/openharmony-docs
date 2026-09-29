# NetStatsInfo

```TypeScript
export interface NetStatsInfo
```

Defines the historical traffic information.

**Since:** 22

<!--Device-statistics-export interface NetStatsInfo--><!--Device-statistics-export interface NetStatsInfo-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## Modules to Import

```TypeScript
import { statistics } from '@kit.NetworkKit';
```

## rxBytes

```TypeScript
rxBytes: number
```

Downlink traffic data (unit: bytes).

**Type:** number

**Since:** 22

<!--Device-NetStatsInfo-rxBytes: long--><!--Device-NetStatsInfo-rxBytes: long-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## rxPackets

```TypeScript
rxPackets: number
```

Number of downlink packets.

**Type:** number

**Since:** 22

<!--Device-NetStatsInfo-rxPackets: long--><!--Device-NetStatsInfo-rxPackets: long-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## txBytes

```TypeScript
txBytes: number
```

Uplink traffic data (unit: bytes).

**Type:** number

**Since:** 22

<!--Device-NetStatsInfo-txBytes: long--><!--Device-NetStatsInfo-txBytes: long-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## txPackets

```TypeScript
txPackets: number
```

Number of uplink packets.

**Type:** number

**Since:** 22

<!--Device-NetStatsInfo-txPackets: long--><!--Device-NetStatsInfo-txPackets: long-End-->

**System capability:** SystemCapability.Communication.NetManager.Core
