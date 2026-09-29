# SyncResult

```TypeScript
interface SyncResult
```

Represents the sync result of an asset.

**Since:** 20

<!--Device-asset-interface SyncResult--><!--Device-asset-interface SyncResult-End-->

**System capability:** SystemCapability.Security.Asset

## Modules to Import

```TypeScript
import { asset } from '@kit.AssetStoreKit';
```

## failedCount

```TypeScript
readonly failedCount?: number
```

Number of assets that fail to be synced.

**Type:** number

**Since:** 20

<!--Device-SyncResult-readonly failedCount?: number--><!--Device-SyncResult-readonly failedCount?: number-End-->

**System capability:** SystemCapability.Security.Asset

## resultCode

```TypeScript
readonly resultCode: number
```

Sync result code of an asset. If the sync is successful, the result code is **0**. If the sync fails, see [ErrorCode](arkts-assetstore-asset-errorcode-e.md) for the result code.

**Type:** number

**Since:** 20

<!--Device-SyncResult-readonly resultCode: number--><!--Device-SyncResult-readonly resultCode: number-End-->

**System capability:** SystemCapability.Security.Asset

## totalCount

```TypeScript
readonly totalCount?: number
```

Total number of assets to be synced.

**Type:** number

**Since:** 20

<!--Device-SyncResult-readonly totalCount?: number--><!--Device-SyncResult-readonly totalCount?: number-End-->

**System capability:** SystemCapability.Security.Asset
