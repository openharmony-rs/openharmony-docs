# OH_PictureNative_MetadataCopyItem

```c
typedef struct OH_PictureNative_MetadataCopyItem {...} OH_PictureNative_MetadataCopyItem
```

## Overview

This structure is used to specify a metadata copy rule when creating a deep copy of a PictureNative object. It describes how to copy metadata from one type to another.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 26.0.0

**Related module**: [Image_NativeModule](capi-image-nativemodule.md)

**Header file**: [picture_native.h](capi-picture-native-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| Image_MetadataType srcType | Source metadata type. It specifies the type of metadata to be copied from the source picture.<br>**Since**: 26.0.0 |
| Image_MetadataType dstType | Destination metadata type. It specifies the type under which the copied metadata will be stored in the destination picture.<br>**Since**: 26.0.0 |


