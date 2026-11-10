# Asset_Result

```c
typedef struct Asset_Result {...} Asset_Result
```

## Overview

Represents the query result of an asset.

<!--Device-typedef struct Asset_Result {...} Asset_Result--><!--Device-typedef struct Asset_Result {...} Asset_Result-End-->

**System capability**: SystemCapability.Security.Asset

**Since**: 11

**Related module**: [AssetType](capi-asset-store-kit-assettype.md)

**Header file**: [asset_type.h](capi-asset-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t count | Number of asset attributes in the query result. |
| Asset_Attr *attrs | Pointer to the array of the asset attributes. |


