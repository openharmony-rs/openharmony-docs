# VkNativeBufferOHOS

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @andrew1993-->
<!--Designer: @ext4FAT1-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

```c
typedef struct VkNativeBufferOHOS {...} VkNativeBufferOHOS
```

## Overview

Describes the parameters of the native display buffer.

**Since**: 10

**Related module**: [Vulkan](capi-vulkan.md)

**Header file**: [vulkan_ohos.h](capi-vulkan-ohos-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| VkStructureType sType | Struct type.|
| const void*        pNext | Pointer to the next-level struct; **pNext** is either null or a pointer to the next-level struct.|
| struct [OHBufferHandle*](capi-vulkan-ohbufferhandle.md)      handle | Device memory handle.|
