# VkSurfaceCreateInfoOHOS

```c
typedef struct VkSurfaceCreateInfoOHOS {...} VkSurfaceCreateInfoOHOS
```

## Overview

Defines the parameters required for creating a Vulkan surface.

**Since**: 10

**Related module**: [Vulkan](capi-vulkan.md)

**Header file**: [vulkan_ohos.h](capi-vulkan-ohos-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| VkStructureType sType | Struct sType is a VkStructureType value identifying this structure. it must be VK_STRUCTURE_TYPE_SURFACE_CREATE_INFO_OHOS. |
| const void* pNext | pNext is NULL or a pointer to a structure extending this structure. pNext must be NULL. |
| VkSurfaceCreateFlagsOHOS flags | flags is reserved for future use. flags must be 0. |
| [OHNativeWindow*](capi-vulkan-nativewindow.md) window | window: is a pointer to a OHNativeWindow to associate the surface with. |


