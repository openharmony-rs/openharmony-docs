# Asset_Blob

<!--Kit: Asset Store Kit-->
<!--Subsystem: Security-->
<!--Owner: @HarMonkey-->
<!--Designer: @wkr321_ent-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=d910972754a03f29eabea013ac43af463c14ec75 translatedAt=2026-11-06T11:52:05.913Z pushedAt=2026-11-09T11:56:36.422Z nl=1 -->

```c
typedef struct {...} Asset_Blob
```

## Overview

Defines a binary array, that is, an array of bytes with variable length.

**Since**: 11

**Related module**: [AssetType](capi-assettype.md)

**Header file:** [asset_type.h](capi-asset-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t size | Size of the byte array.|
| uint8_t *data | Pointer to the byte array.|


