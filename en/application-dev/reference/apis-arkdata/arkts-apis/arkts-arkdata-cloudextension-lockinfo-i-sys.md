# LockInfo (System API)

```TypeScript
export interface LockInfo
```

Represents the cloud database lock information.

**Since:** 11

<!--Device-cloudExtension-export interface LockInfo--><!--Device-cloudExtension-export interface LockInfo-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

## interval

```TypeScript
interval: number
```

Lock period of the cloud database, in seconds.

**Type:** number

**Since:** 11

<!--Device-LockInfo-interval: int--><!--Device-LockInfo-interval: int-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

## lockId

```TypeScript
lockId: number
```

Lock ID.

**Type:** number

**Since:** 11

<!--Device-LockInfo-lockId: int--><!--Device-LockInfo-lockId: int-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.
