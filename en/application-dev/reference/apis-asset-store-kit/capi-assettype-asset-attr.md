# Asset_Attr

<!--Kit: Asset Store Kit-->
<!--Subsystem: Security-->
<!--Owner: @HarMonkey-->
<!--Designer: @wkr321_ent-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=fc40c8a1c3aad9cf93b514f99c4b41f2d7bdfca0 translatedAt=2026-11-16T04:12:34.845Z pushedAt=2026-11-16T06:31:14.001Z nl=1 -->

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


