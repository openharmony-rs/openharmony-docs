# VkSurfaceCreateInfoOHOS

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @andrew1993-->
<!--Designer: @ext4FAT1-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

```c
typedef struct VkSurfaceCreateInfoOHOS {...} VkSurfaceCreateInfoOHOS
```

## Overview

The struct describes the parameters required for creating a Vulkan surface.

**Since**: 10

**Related module**: [Vulkan](capi-vulkan.md)

**Header file**: [vulkan_ohos.h](capi-vulkan-ohos-h.md)

## Summary

### Member Variables

| Name                            | Description|
|--------------------------------| -- |
| VkStructureType sType          | Struct type. The value must be **VK_STRUCTURE_TYPE_SURFACE_CREATE_INFO_OHOS**.|
| const void* pNext              | Pointer to the next struct in the chain. The value must be nullptr.|
| VkSurfaceCreateFlagsOHOS flags | Reserved flags. The value must be **0**.|
| [OHNativeWindow](capi-vulkan-nativewindow.md)* window     | Pointer to an OHNativeWindow instance.|
