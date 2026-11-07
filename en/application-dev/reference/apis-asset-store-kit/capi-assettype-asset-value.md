# Asset_Value

<!--Kit: Asset Store Kit-->
<!--Subsystem: Security-->
<!--Owner: @HarMonkey-->
<!--Designer: @wkr321_ent-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=fc40c8a1c3aad9cf93b514f99c4b41f2d7bdfca0 translatedAt=2026-11-04T12:06:06.124Z pushedAt=2026-11-04T12:07:10.516Z nl=1 -->

```c
typedef union {...} Asset_Value
```

## Overview

The value (content) of a key asset attribute.

**Since**: 11

**Related module**: [AssetType](capi-assettype.md)

**Header file:** [asset_type.h](capi-asset-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| bool boolean | This field is used to pass a bool-type attribute value. |
| uint32_t u32 | This field is used to pass a uint32-type attribute value. |
| [Asset_Blob](capi-assettype-asset-blob.md) blob | This field is used to pass a bytes-type attribute value. |


