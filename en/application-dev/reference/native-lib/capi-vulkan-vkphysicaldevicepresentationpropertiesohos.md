# VkPhysicalDevicePresentationPropertiesOHOS

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @andrew1993-->
<!--Designer: @ext4FAT1-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

```c
typedef struct VkPhysicalDevicePresentationPropertiesOHOS {...} VkPhysicalDevicePresentationPropertiesOHOS
```

## Overview

Describes the parameters of the device display properties.

**Since**: 10

**Related module**: [Vulkan](capi-vulkan.md)

**Header file**: [vulkan_ohos.h](capi-vulkan-ohos-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| VkStructureType sType | Pointer to the next-level struct; **pNext** is either null or a pointer to the next-level struct.|
| VkBool32 sharedImage | Shared image flag.|
