# OH_NativeBuffer_Config

```c
typedef struct OH_NativeBuffer_Config {...} OH_NativeBuffer_Config
```

## Overview

<b>OH_NativeBuffer</b> config. Used to allocating new <b>OH_NativeBuffer</b> and query parameters if existing ones.

**Since**: 9

**Related module**: [OH_NativeBuffer](capi-oh-nativebuffer.md)

**Header file**: [native_buffer.h](capi-native-buffer-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t width | Width in pixels |
| int32_t height | Height in pixels |
| int32_t format | One of PixelFormat |
| int32_t usage | Combination of buffer usage |
| int32_t stride |  |


