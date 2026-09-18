# NetworkInfo

Defines the network information.

**Since:** 22

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

**System capability:** SystemCapability.Communication.NetManager.Core

## simId

```TypeScript
simId?: number
```

SIM card ID. The default value is the maximum value of the uint32_t type.

**Note:**  If **type** is set to **cellular**, this field must be specified.

**Type:** number

**Since:** 22

**System capability:** SystemCapability.Communication.NetManager.Core

## startTime

```TypeScript
startTime: number
```

Start timestamp, in seconds.

**Type:** number

**Since:** 22

**System capability:** SystemCapability.Communication.NetManager.Core

## type

```TypeScript
type: NetBearType
```

Network type.

**Note:**  If **type** is set to **cellular**, the **simId** field must be specified.

**Type:** [NetBearType](arkts-network-statistics-netbeartype-t.md)

**Since:** 22

**System capability:** SystemCapability.Communication.NetManager.Core
