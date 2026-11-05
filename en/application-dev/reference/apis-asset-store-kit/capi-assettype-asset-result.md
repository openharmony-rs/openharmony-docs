# Asset_Result

<!--Kit: Asset Store Kit-->
<!--Subsystem: Security-->
<!--Owner: @HarMonkey-->
<!--Designer: @wkr321_ent-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=fc40c8a1c3aad9cf93b514f99c4b41f2d7bdfca0 translatedAt=2026-11-04T12:05:22.922Z pushedAt=2026-11-04T12:07:03.484Z nl=1 -->

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


