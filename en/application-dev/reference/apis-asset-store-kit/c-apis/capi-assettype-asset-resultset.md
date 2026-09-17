# Asset_ResultSet

```c
typedef struct Asset_ResultSet {...} Asset_ResultSet
```

## Overview

Represents the query result of multiple assets.

**Since**: 11

**Related module**: [AssetType](capi-assettype.md)

**Header file**: [asset_type.h](capi-asset-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t count | Number of assets in the query result. |
| [Asset_Result](capi-assettype-asset-result.md) *results | Pointer to the array of the assets. |


