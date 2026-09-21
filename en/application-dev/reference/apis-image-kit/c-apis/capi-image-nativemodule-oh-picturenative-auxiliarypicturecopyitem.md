# OH_PictureNative_AuxiliaryPictureCopyItem

```c
typedef struct OH_PictureNative_AuxiliaryPictureCopyItem {...} OH_PictureNative_AuxiliaryPictureCopyItem
```

## Overview

This structure is used to specify an auxiliary picture copy rule when creating a deep copy of a PictureNative object. It describes how to copy an auxiliary picture from one type to another.

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 26.0.0

**Related module**: [Image_NativeModule](capi-image-nativemodule.md)

**Header file**: [picture_native.h](capi-picture-native-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [Image_AuxiliaryPictureType](capi-picture-native-h.md#image_auxiliarypicturetype) srcType | Source auxiliary picture type. It specifies the type of auxiliary picture to be copied from the source picture.<br>**Since**: 26.0.0 |
| [Image_AuxiliaryPictureType](capi-picture-native-h.md#image_auxiliarypicturetype) dstType | Destination auxiliary picture type. It specifies the type under which the copied auxiliary picture will be stored in the destination picture.<br>**Since**: 26.0.0 |


