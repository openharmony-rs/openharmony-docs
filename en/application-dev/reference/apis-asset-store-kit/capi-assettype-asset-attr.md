# Asset_Attr

<!--Kit: Asset Store Kit-->
<!--Subsystem: Security-->
<!--Owner: @HarMonkey-->
<!--Designer: @wkr321_ent-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=878a214020b090430fbfc011fb9e9d5b26ec4594 translatedAt=2026-11-06T11:51:37.140Z pushedAt=2026-11-09T11:56:16.664Z nl=1 -->

```c
typedef struct {...} Asset_Attr
```

## Overview

Critical asset attribute. An attribute consists of a tag and a value, and exists in the form of a key-value pair.

**Since**: 11

**Related module**: [AssetType](capi-assettype.md)

**Header file:** [asset_type.h](capi-asset-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t tag | Tag of the critical asset attribute. |
| [Asset_Value](capi-assettype-asset-value.md) value | The value (content) of a key asset attribute. |


