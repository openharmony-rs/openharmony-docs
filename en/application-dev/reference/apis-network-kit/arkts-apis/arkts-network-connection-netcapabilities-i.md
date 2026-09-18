# NetCapabilities

Defines the network capability set.

**Since:** 8

**System capability:** SystemCapability.Communication.NetManager.Core

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## bearerTypes

```TypeScript
bearerTypes: Array<NetBearType>
```

Network type. The array contains only one network type.

**Type:** Array&lt;[NetBearType](arkts-network-connection-netbeartype-e.md)&gt;

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.Core

## linkDownBandwidthKbps

```TypeScript
linkDownBandwidthKbps?: number
```

Downlink (network-to-device) bandwidth, in kbit/s. The value **0** indicates that the current network bandwidth cannot be evaluated.

**Type:** number

**Since:** 8

**System capability:** SystemCapability.Communication.NetManager.Core

## linkUpBandwidthKbps

```TypeScript
linkUpBandwidthKbps?: number
```

Uplink (device-to-network) bandwidth, in kbit/s. The value **0** indicates that the current network bandwidth cannot be evaluated.

**Type:** number

**Since:** 8

**System capability:** SystemCapability.Communication.NetManager.Core

## networkCap

```TypeScript
networkCap?: Array<NetCap>
```

Network capability.

**Type:** Array&lt;[NetCap](arkts-network-connection-netcap-e.md)&gt;

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.Core
