# Asset_ResultSet

<!--Kit: Asset Store Kit-->
<!--Subsystem: Security-->
<!--Owner: @HarMonkey-->
<!--Designer: @wkr321_ent-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=fc40c8a1c3aad9cf93b514f99c4b41f2d7bdfca0 translatedAt=2026-11-16T04:18:30.583Z pushedAt=2026-11-16T06:31:14.006Z nl=1 -->

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


