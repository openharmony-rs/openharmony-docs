# VkExternalFormatOHOS

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @andrew1993-->
<!--Designer: @ext4FAT1-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

```c
typedef struct VkExternalFormatOHOS {...} VkExternalFormatOHOS
```

## Overview

The struct describes an externally defined format.

**Since**: 10

**Related module**: [Vulkan](capi-vulkan.md)

**Header file**: [vulkan_ohos.h](capi-vulkan-ohos-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| VkStructureType sType | Struct type. The value must be **VK_STRUCTURE_TYPE_EXTERNAL_FORMAT_OHOS**.|
| void* pNext | Either nullptr or a pointer to the next struct in the chain.|
| uint64_t externalFormat | Externally defined format.|
