# Asset_Attr

```c
typedef struct Asset_Attr {...} Asset_Attr
```

## Overview

Defines an asset attribute, which consists of a tag and a value in the form of a key-value (KV) pair.

**Since**: 11

**Related module**: [AssetType](capi-assettype.md)

**Header file**: [asset_type.h](capi-asset-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t tag | The tag of an asset attribute. |
| [Asset_Value](capi-assettype-asset-value.md) value | The value (content) of an asset attribute. |


