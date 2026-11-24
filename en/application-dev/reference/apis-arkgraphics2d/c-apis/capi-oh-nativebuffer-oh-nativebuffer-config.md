# OH_NativeBuffer_Config

```c
typedef struct OH_NativeBuffer_Config {...} OH_NativeBuffer_Config
```

## Overview

<b>OH_NativeBuffer</b> config. Used to allocating new <b>OH_NativeBuffer</b> and query parameters if existing ones.

<!--Device-typedef struct OH_NativeBuffer_Config {...} OH_NativeBuffer_Config--><!--Device-typedef struct OH_NativeBuffer_Config {...} OH_NativeBuffer_Config-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeBuffer

**Since**: 9

**Related module**: [OH_NativeBuffer](capi-arkgraphics2d-oh-nativebuffer.md)

**Header file**: [native_buffer.h](capi-native-buffer-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t width | Width in pixels<br><!--Device-int32_t width--><!--Device-int32_t width-End--> |
| int32_t height | Height in pixels<br><!--Device-int32_t height--><!--Device-int32_t height-End--> |
| int32_t format | One of PixelFormat<br><!--Device-int32_t format--><!--Device-int32_t format-End--> |
| int32_t usage | Combination of buffer usage<br><!--Device-int32_t usage--><!--Device-int32_t usage-End--> |
| int32_t stride | the stride of memory in bytes<br>**Since**: 10<br><!--Device-int32_t stride--><!--Device-int32_t stride-End--> |


