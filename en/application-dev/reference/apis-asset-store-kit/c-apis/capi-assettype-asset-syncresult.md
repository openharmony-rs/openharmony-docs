# Asset_SyncResult

```c
typedef struct Asset_SyncResult {...} Asset_SyncResult
```

## Overview

Represents the sync result of an asset.

<!--Device-typedef struct Asset_SyncResult {...} Asset_SyncResult--><!--Device-typedef struct Asset_SyncResult {...} Asset_SyncResult-End-->

**System capability**: SystemCapability.Security.Asset

**Since**: 20

**Related module**: [AssetType](capi-asset-store-kit-assettype.md)

**Header file**: [asset_type.h](capi-asset-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t resultCode | Sync result code of an asset. If the synchronization is successful, the result code is 0. For details about the result code when the synchronization fails, see Asset_ResultCode.<br><!--Device-int32_t resultCode--><!--Device-int32_t resultCode-End--> |
| uint32_t totalCount | Total number of assets to be synced.<br><!--Device-uint32_t totalCount--><!--Device-uint32_t totalCount-End--> |
| uint32_t failedCount | Number of assets that fail to be synced.<br><!--Device-uint32_t failedCount--><!--Device-uint32_t failedCount-End--> |


