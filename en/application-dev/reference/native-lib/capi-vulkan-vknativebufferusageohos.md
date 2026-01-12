# VkNativeBufferUsageOHOS

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @andrew1993-->
<!--Designer: @ext4FAT1-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

```c
typedef struct VkNativeBufferUsageOHOS {...} VkNativeBufferUsageOHOS
```

## Overview

The struct describes the usage of the NativeBuffer.

**Since**: 10

**Related module**: [Vulkan](capi-vulkan.md)

**Header file**: [vulkan_ohos.h](capi-vulkan-ohos-h.md)

## Summary

### Member Variables

| Name| Description|
|----| -- |
| VkStructureType sType   | Struct type. The value must be **VK_STRUCTURE_TYPE_NATIVE_BUFFER_USAGE_OHOS**.|
| void* pNext   | Pointer to the next-level struct.|
| uint64_t OHOSNativeBufferUsage  | Usage of the NativeBuffer.|
