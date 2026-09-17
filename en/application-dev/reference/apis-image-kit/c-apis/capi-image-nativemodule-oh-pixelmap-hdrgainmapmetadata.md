# OH_Pixelmap_HdrGainmapMetadata

```c
typedef struct OH_Pixelmap_HdrGainmapMetadata {...} OH_Pixelmap_HdrGainmapMetadata
```

## Overview

Value for HDR_GAINMAP_METADATA.

**Since**: 12

**Related module**: [Image_NativeModule](capi-image-nativemodule.md)

**Header file**: [pixelmap_native.h](capi-pixelmap-native-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint16_t writerVersion | The version used by the writer. |
| uint16_t miniVersion | The minimum version a parser needs to understand. |
| uint8_t gainmapChannelNum | The number of gain map channels, with a value of 1 or 3. |
| bool useBaseColorFlag | Indicate whether to use the color space of the base image. |
| float baseHeadroom | The baseline hdr headroom. |
| float alternateHeadroom | The alternate hdr headroom. |
| float gainmapMax[3] | The per-component max gain map values. |
| float gainmapMin[3] | The per-component min gain map values. |
| float gamma[3] | The per-component gamma values. |
| float baselineOffset[3] | The per-component baseline offset. |
| float alternateOffset[3] | The per-component alternate offset. |


