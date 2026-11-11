# Asset_ResultSet

<!--Kit: Asset Store Kit-->
<!--Subsystem: Security-->
<!--Owner: @HarMonkey-->
<!--Designer: @wkr321_ent-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=878a214020b090430fbfc011fb9e9d5b26ec4594 translatedAt=2026-11-06T11:53:35.390Z pushedAt=2026-11-09T11:47:58.427Z nl=1 -->

```c
typedef struct {...} Asset_ResultSet
```

## Overview

Query result of multiple critical assets.

**Since**: 11

**Related module**: [AssetType](capi-assettype.md)

**Header file:** [asset_type.h](capi-asset-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t count | Number of assets in the query result.|
| [Asset_Result](capi-assettype-asset-result.md) *results | Pointer to the array of assets.|


