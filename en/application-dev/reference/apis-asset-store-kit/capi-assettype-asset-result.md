# Asset_Result

<!--Kit: Asset Store Kit-->
<!--Subsystem: Security-->
<!--Owner: @HarMonkey-->
<!--Designer: @wkr321_ent-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=878a214020b090430fbfc011fb9e9d5b26ec4594 translatedAt=2026-11-06T11:53:22.679Z pushedAt=2026-11-09T11:47:17.402Z nl=1 -->

```c
typedef struct {...} Asset_Result
```

## Overview

Query result of a single critical asset.

**Since**: 11

**Related module**: [AssetType](capi-assettype.md)

**Header file:** [asset_type.h](capi-asset-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t count | Number of asset attributes in the query result.|
| [Asset_Attr](capi-assettype-asset-attr.md) *attrs | Pointer to the array of the asset attributes.|


