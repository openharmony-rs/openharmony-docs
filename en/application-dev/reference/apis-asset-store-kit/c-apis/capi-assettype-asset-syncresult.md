# Asset_SyncResult

```c
typedef struct Asset_SyncResult {...} Asset_SyncResult
```

## Overview

Represents the sync result of an asset.

**System capability**: SystemCapability.Security.Asset

**Since**: 20

**Related module**: [AssetType](capi-assettype.md)

**Header file**: [asset_type.h](capi-asset-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t resultCode | Sync result code of an asset. If the synchronization is successful, the result code is 0. For details about the result code when the synchronization fails, see Asset_ResultCode. |
| uint32_t totalCount | Total number of assets to be synced. |
| uint32_t failedCount | Number of assets that fail to be synced. |


