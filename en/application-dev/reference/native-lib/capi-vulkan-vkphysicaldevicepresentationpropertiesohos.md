# VkPhysicalDevicePresentationPropertiesOHOS

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @andrew1993-->
<!--Designer: @ext4FAT1-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=3d4a9824857ce59e497945f30834304869ed7256 translatedAt=2026-10-09T12:48:40.523Z pushedAt=2026-10-10T10:08:08.508Z -->

```c
typedef struct VkPhysicalDevicePresentationPropertiesOHOS {...} VkPhysicalDevicePresentationPropertiesOHOS
```

## Overview

Describes the parameters of the device display properties.

**Since**: 10

**Deprecated:** 23 

**Related module**: [Vulkan](capi-vulkan.md)

**Header file**: [vulkan_ohos.h](capi-vulkan-ohos-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| VkStructureType sType | Structure type. |
| void* pNext    | Pointer to the next-level struct. It can be null or point to the next-level struct. |
| VkBool32 sharedImage | Shared image flag.|