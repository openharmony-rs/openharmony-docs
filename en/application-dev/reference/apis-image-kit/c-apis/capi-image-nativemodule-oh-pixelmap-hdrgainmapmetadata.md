# OH_Pixelmap_HdrGainmapMetadata

```c
typedef struct OH_Pixelmap_HdrGainmapMetadata {...} OH_Pixelmap_HdrGainmapMetadata
```

## Overview

Value for HDR_GAINMAP_METADATA.

<!--Device-struct OH_Pixelmap_HdrGainmapMetadata {...}--><!--Device-struct OH_Pixelmap_HdrGainmapMetadata {...}-End-->

**System capability**: SystemCapability.Multimedia.Image.Core

**Since**: 12

**Related module**: [Image_NativeModule](capi-image-kit-image-nativemodule.md)

**Header file**: [pixelmap_native.h](capi-pixelmap-native-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint16_t writerVersion | The version used by the writer.<br><!--Device-uint16_t writerVersion--><!--Device-uint16_t writerVersion-End--> |
| uint16_t miniVersion | The minimum version a parser needs to understand.<br><!--Device-uint16_t miniVersion--><!--Device-uint16_t miniVersion-End--> |
| uint8_t gainmapChannelNum | The number of gain map channels, with a value of 1 or 3.<br><!--Device-uint8_t gainmapChannelNum--><!--Device-uint8_t gainmapChannelNum-End--> |
| bool useBaseColorFlag | Indicate whether to use the color space of the base image.<br><!--Device-bool useBaseColorFlag--><!--Device-bool useBaseColorFlag-End--> |
| float baseHeadroom | The baseline hdr headroom.<br><!--Device-float baseHeadroom--><!--Device-float baseHeadroom-End--> |
| float alternateHeadroom | The alternate hdr headroom.<br><!--Device-float alternateHeadroom--><!--Device-float alternateHeadroom-End--> |
| float gainmapMax[3] | The per-component max gain map values.<br><!--Device-float gainmapMax[3]--><!--Device-float gainmapMax[3]-End--> |
| float gainmapMin[3] | The per-component min gain map values.<br><!--Device-float gainmapMin[3]--><!--Device-float gainmapMin[3]-End--> |
| float gamma[3] | The per-component gamma values.<br><!--Device-float gamma[3]--><!--Device-float gamma[3]-End--> |
| float baselineOffset[3] | The per-component baseline offset.<br><!--Device-float baselineOffset[3]--><!--Device-float baselineOffset[3]-End--> |
| float alternateOffset[3] | The per-component alternate offset.<br><!--Device-float alternateOffset[3]--><!--Device-float alternateOffset[3]-End--> |


