# VkMemoryGetNativeBufferInfoOHOS

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @andrew1993-->
<!--Designer: @ext4FAT1-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

```c
typedef struct VkMemoryGetNativeBufferInfoOHOS {...} VkMemoryGetNativeBufferInfoOHOS
```

## Overview

The struct is used to obtain an OH_NativeBuffer from the Vulkan memory.

**Since**: 10

**Related module**: [Vulkan](capi-vulkan.md)

**Header file**: [vulkan_ohos.h](capi-vulkan-ohos-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| VkStructureType sType | Struct type. The value must be **VK_STRUCTURE_TYPE_MEMORY_GET_NATIVE_BUFFER_INFO_OHOS**.|
| const void* pNext | Pointer to the next struct in the chain. The value must be nullptr.|
| VkDeviceMemory memory | VkDeviceMemory object. The value must be a valid VkDeviceMemory object.|
