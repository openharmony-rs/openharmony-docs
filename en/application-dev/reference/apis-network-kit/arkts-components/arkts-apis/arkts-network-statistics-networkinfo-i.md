# NetworkInfo

```TypeScript
export interface NetworkInfo
```

Defines the network information.

**Since:** 22

<!--Device-statistics-export interface NetworkInfo--><!--Device-statistics-export interface NetworkInfo-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## Modules to Import

```TypeScript
import { statistics } from '@kit.NetworkKit';
```

## endTime

```TypeScript
endTime: number
```

End timestamp, in seconds.

**Type:** number

**Since:** 22

<!--Device-NetworkInfo-endTime: int--><!--Device-NetworkInfo-endTime: int-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## simId

```TypeScript
simId?: number
```

SIM card ID. The default value is the maximum value of the uint32_t type.

**Note:**  If **type** is set to **cellular**, this field must be specified.

**Type:** number

**Since:** 22

<!--Device-NetworkInfo-simId?: int--><!--Device-NetworkInfo-simId?: int-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## startTime

```TypeScript
startTime: number
```

Start timestamp, in seconds.

**Type:** number

**Since:** 22

<!--Device-NetworkInfo-startTime: int--><!--Device-NetworkInfo-startTime: int-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## type

```TypeScript
type: NetBearType
```

Network type.

**Note:**  If **type** is set to **cellular**, the **simId** field must be specified.

**Type:** [NetBearType](arkts-network-statistics-netbeartype-t.md)

**Since:** 22

<!--Device-NetworkInfo-type: NetBearType--><!--Device-NetworkInfo-type: NetBearType-End-->

**System capability:** SystemCapability.Communication.NetManager.Core
