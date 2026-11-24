# VkSurfaceCreateInfoOHOS

```c
typedef struct VkSurfaceCreateInfoOHOS {...} VkSurfaceCreateInfoOHOS
```

## Overview

Defines the parameters required for creating a Vulkan surface.

<!--Device-struct VkSurfaceCreateInfoOHOS {...}--><!--Device-struct VkSurfaceCreateInfoOHOS {...}-End-->

**System capability**: SystemCapability.Graphic.Vulkan

**Since**: 10

**Related module**: [Vulkan](capi-arkgraphics2d-vulkan.md)

**Header file**: [vulkan_ohos.h](capi-vulkan-ohos-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| VkStructureType sType | Struct sType is a VkStructureType value identifying this structure. it must be VK_STRUCTURE_TYPE_SURFACE_CREATE_INFO_OHOS.<br><!--Device-VkStructureType sType--><!--Device-VkStructureType sType-End--> |
| const void* pNext | pNext is NULL or a pointer to a structure extending this structure. pNext must be NULL.<br><!--Device-const void* pNext--><!--Device-const void* pNext-End--> |
| VkSurfaceCreateFlagsOHOS flags | flags is reserved for future use. flags must be 0.<br><!--Device-VkSurfaceCreateFlagsOHOS flags--><!--Device-VkSurfaceCreateFlagsOHOS flags-End--> |
| [OHNativeWindow*](capi-vulkan-nativewindow.md) window | window: is a pointer to a OHNativeWindow to associate the surface with.<br><!--Device-OHNativeWindow* window--><!--Device-OHNativeWindow* window-End--> |


