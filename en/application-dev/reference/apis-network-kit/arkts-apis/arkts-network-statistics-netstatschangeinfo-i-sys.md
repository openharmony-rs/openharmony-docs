# NetStatsChangeInfo (System API)

```TypeScript
export interface NetStatsChangeInfo
```

Defines the NIC status and usage of an application.

**Since:** 11

<!--Device-statistics-export interface NetStatsChangeInfo--><!--Device-statistics-export interface NetStatsChangeInfo-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { statistics } from '@kit.NetworkKit';
```

## iface

```TypeScript
iface: string
```

NIC name.

**Type:** string

**Since:** 11

<!--Device-NetStatsChangeInfo-iface: string--><!--Device-NetStatsChangeInfo-iface: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.

## uid

```TypeScript
uid?: number
```

Application UID.

**Type:** number

**Since:** 11

<!--Device-NetStatsChangeInfo-uid?: int--><!--Device-NetStatsChangeInfo-uid?: int-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

**System API:** This is a system API.
