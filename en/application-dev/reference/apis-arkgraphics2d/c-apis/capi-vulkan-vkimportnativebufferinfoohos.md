# VkImportNativeBufferInfoOHOS

```c
typedef struct VkImportNativeBufferInfoOHOS {...} VkImportNativeBufferInfoOHOS
```

## Overview

Defines the pointer to an <b>OH_NativeBuffer</b> struct.

<!--Device-struct VkImportNativeBufferInfoOHOS {...}--><!--Device-struct VkImportNativeBufferInfoOHOS {...}-End-->

**System capability**: SystemCapability.Graphic.Vulkan

**Since**: 10

**Related module**: [Vulkan](capi-arkgraphics2d-vulkan.md)

**Header file**: [vulkan_ohos.h](capi-vulkan-ohos-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| VkStructureType            sType | Struct type.<br><!--Device-VkStructureType sType--><!--Device-VkStructureType sType-End--> |
| const void*                pNext | Pointer to the next-level struct.<br><!--Device-const void* pNext--><!--Device-const void* pNext-End--> |
| [struct OH_NativeBuffer*](capi-vulkan-oh-nativebuffer.md)    buffer | Pointer to an <b>OH_NativeBuffer</b> struct.<br><!--Device-struct OH_NativeBuffer* buffer--><!--Device-struct OH_NativeBuffer* buffer-End--> |


