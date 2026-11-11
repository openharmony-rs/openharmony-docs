# VkSwapchainImageCreateInfoOHOS

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @andrew1993-->
<!--Designer: @ext4FAT1-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=3d4a9824857ce59e497945f30834304869ed7256 translatedAt=2026-11-06T12:13:29.646Z pushedAt=2026-11-09T11:49:21.612Z nl=1 -->

```c
typedef struct VkSwapchainImageCreateInfoOHOS {...} VkSwapchainImageCreateInfoOHOS
```

## Overview

Describes the parameters required for creating an image.

**Since**: 10

**Deprecated since:** 23

**Related module**: [Vulkan](capi-vulkan.md)

**Header file**: [vulkan_ohos.h](capi-vulkan-ohos-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| VkStructureType sType | Struct type.|
| const void*                       pNext | Pointer to the next-level struct; **pNext** is either null or a pointer to the next-level struct.|
| VkSwapchainImageUsageFlagsOHOS usage | Usage flags of the swapchain image.|