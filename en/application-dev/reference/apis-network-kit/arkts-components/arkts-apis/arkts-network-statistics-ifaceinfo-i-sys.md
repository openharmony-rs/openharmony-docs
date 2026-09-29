# IfaceInfo (System API)

```TypeScript
export interface IfaceInfo
```

Defines the parameters for querying historical traffic of an NIC.

**Since:** 10

<!--Device-statistics-export interface IfaceInfo--><!--Device-statistics-export interface IfaceInfo-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { statistics } from '@kit.NetworkKit';
```

## endTime

```TypeScript
endTime: number
```

End time of the query, which is a timestamp in seconds.

**Type:** number

**Since:** 10

<!--Device-IfaceInfo-endTime: int--><!--Device-IfaceInfo-endTime: int-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## iface

```TypeScript
iface: string
```

NIC name.

**Type:** string

**Since:** 10

<!--Device-IfaceInfo-iface: string--><!--Device-IfaceInfo-iface: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## startTime

```TypeScript
startTime: number
```

Start time of the query, which is a timestamp in seconds.

**Type:** number

**Since:** 10

<!--Device-IfaceInfo-startTime: int--><!--Device-IfaceInfo-startTime: int-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.
