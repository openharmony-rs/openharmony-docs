# Asset_Value

<!--Kit: Asset Store Kit-->
<!--Subsystem: Security-->
<!--Owner: @HarMonkey-->
<!--Designer: @wkr321_ent-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=878a214020b090430fbfc011fb9e9d5b26ec4594 translatedAt=2026-11-06T11:54:19.021Z pushedAt=2026-11-09T11:48:07.086Z nl=1 -->

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


