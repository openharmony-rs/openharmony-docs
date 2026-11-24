# VkExternalFormatOHOS

```c
typedef struct VkExternalFormatOHOS {...} VkExternalFormatOHOS
```

## Overview

Defines an externally defined format.

<!--Device-struct VkExternalFormatOHOS {...}--><!--Device-struct VkExternalFormatOHOS {...}-End-->

**System capability**: SystemCapability.Graphic.Vulkan

**Since**: 10

**Related module**: [Vulkan](capi-arkgraphics2d-vulkan.md)

**Header file**: [vulkan_ohos.h](capi-vulkan-ohos-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| VkStructureType sType | sType is a VkStructureType value identifying this structure. sType must be VK_STRUCTURE_TYPE_EXTERNAL_FORMAT_OHOS.<br><!--Device-VkStructureType sType--><!--Device-VkStructureType sType-End--> |
| void* pNext | pNext is NULL or a pointer to a structure extending this structure.<br><!--Device-void* pNext--><!--Device-void* pNext-End--> |
| uint64_t externalFormat | externalFormat is an implementation-defined identifier for the external format.<br><!--Device-uint64_t externalFormat--><!--Device-uint64_t externalFormat-End--> |


