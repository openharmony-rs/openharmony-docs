# Asset_SyncResult

<!--Kit: Asset Store Kit-->
<!--Subsystem: Security-->
<!--Owner: @HarMonkey-->
<!--Designer: @wkr321_ent-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=30e973b2521d5f2ec43f64a90ac6d68103fc01d0 translatedAt=2026-11-16T04:19:30.064Z pushedAt=2026-11-16T06:31:14.008Z nl=1 -->

```c
typedef struct {...} Asset_SyncResult
```

## Overview

Represents the sync result of an asset.

**Since**: 20

**Related module**: [AssetType](capi-assettype.md)

**Header file:** [asset_type.h](capi-asset-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t resultCode | Result code of the critical asset synchronization. The result code is 0 when synchronization succeeds, and when synchronization fails, refer to [Asset_ResultCode](capi-asset-type-h.md#asset_resultcode) for the result code. |
| uint32_t totalCount | Total number of assets to be synced.|
| uint32_t failedCount | Number of assets that fail to be synced.|


