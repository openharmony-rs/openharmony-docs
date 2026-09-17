# OH_Pixelmap_HdrStaticMetadata

```c
typedef struct OH_Pixelmap_HdrStaticMetadata {...} OH_Pixelmap_HdrStaticMetadata
```

## Overview

Value for HDR_STATIC_METADATA.

**Since**: 12

**Related module**: [Image_NativeModule](capi-image-nativemodule.md)

**Header file**: [pixelmap_native.h](capi-pixelmap-native-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| float displayPrimariesX[3] | The X-coordinate of the primary colors. The length of the array is three. Store in the order of r, g, b. |
| float displayPrimariesY[3] | The Y-coordinate of the primary colors. The length of the array is three. Store in the order of r, g, b. |
| float whitePointX | The X-coordinate of the white point value. |
| float whitePointY | The Y-coordinate of the white point value. |
| float maxLuminance | Max luminance. |
| float minLuminance | Min luminance. |
| float maxContentLightLevel | Maximum brightness of displayed content. |
| float maxFrameAverageLightLevel | Maximum average brightness of displayed content. |


