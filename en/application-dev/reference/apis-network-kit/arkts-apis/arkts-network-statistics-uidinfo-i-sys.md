# UidInfo (System API)

```TypeScript
export interface UidInfo
```

Defines the parameters for querying historical traffic of an application.

**Since:** 10

<!--Device-statistics-export interface UidInfo--><!--Device-statistics-export interface UidInfo-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { statistics } from '@kit.NetworkKit';
```

## ifaceInfo

```TypeScript
ifaceInfo: IfaceInfo
```

NIC information, including the NIC name and query time range.

**Type:** [IfaceInfo](arkts-network-statistics-ifaceinfo-i-sys.md)

**Since:** 10

<!--Device-UidInfo-ifaceInfo: IfaceInfo--><!--Device-UidInfo-ifaceInfo: IfaceInfo-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## uid

```TypeScript
uid: number
```

Application UID.

**Type:** number

**Since:** 10

<!--Device-UidInfo-uid: int--><!--Device-UidInfo-uid: int-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.
