# OH_Pixelmap_HdrStaticMetadata

```c
typedef struct OH_Pixelmap_HdrStaticMetadata {...} OH_Pixelmap_HdrStaticMetadata
```

## Overview

Value for HDR_STATIC_METADATA.

<!--Device-struct OH_Pixelmap_HdrStaticMetadata {...}--><!--Device-struct OH_Pixelmap_HdrStaticMetadata {...}-End-->

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Related module**: [Image_NativeModule](capi-image-kit-image-nativemodule.md)

**Header file**: [pixelmap_native.h](capi-pixelmap-native-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| float displayPrimariesX[3] | The X-coordinate of the primary colors. The length of the array is three. Store in the order of r, g, b.<br><!--Device-float displayPrimariesX[3]--><!--Device-float displayPrimariesX[3]-End--> |
| float displayPrimariesY[3] | The Y-coordinate of the primary colors. The length of the array is three. Store in the order of r, g, b.<br><!--Device-float displayPrimariesY[3]--><!--Device-float displayPrimariesY[3]-End--> |
| float whitePointX | The X-coordinate of the white point value.<br><!--Device-float whitePointX--><!--Device-float whitePointX-End--> |
| float whitePointY | The Y-coordinate of the white point value.<br><!--Device-float whitePointY--><!--Device-float whitePointY-End--> |
| float maxLuminance | Max luminance.<br><!--Device-float maxLuminance--><!--Device-float maxLuminance-End--> |
| float minLuminance | Min luminance.<br><!--Device-float minLuminance--><!--Device-float minLuminance-End--> |
| float maxContentLightLevel | Maximum brightness of displayed content.<br><!--Device-float maxContentLightLevel--><!--Device-float maxContentLightLevel-End--> |
| float maxFrameAverageLightLevel | Maximum average brightness of displayed content.<br><!--Device-float maxFrameAverageLightLevel--><!--Device-float maxFrameAverageLightLevel-End--> |


