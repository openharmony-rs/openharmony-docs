# Asset_ResultSet

```c
typedef struct Asset_ResultSet {...} Asset_ResultSet
```

## Overview

Represents the query result of multiple assets.

<!--Device-typedef struct Asset_ResultSet {...} Asset_ResultSet--><!--Device-typedef struct Asset_ResultSet {...} Asset_ResultSet-End-->

**System capability**: SystemCapability.Security.Asset

**Since**: 11

**Related module**: [AssetType](capi-asset-store-kit-assettype.md)

**Header file**: [asset_type.h](capi-asset-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t count | Number of assets in the query result. |
| Asset_Result *results | Pointer to the array of the assets. |


