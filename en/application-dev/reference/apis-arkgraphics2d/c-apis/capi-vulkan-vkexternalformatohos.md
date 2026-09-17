# VkExternalFormatOHOS

```c
typedef struct VkExternalFormatOHOS {...} VkExternalFormatOHOS
```

## Overview

Defines an externally defined format.

**Since**: 10

**Related module**: [Vulkan](capi-vulkan.md)

**Header file**: [vulkan_ohos.h](capi-vulkan-ohos-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| VkStructureType sType | sType is a VkStructureType value identifying this structure. sType must be VK_STRUCTURE_TYPE_EXTERNAL_FORMAT_OHOS. |
| void* pNext | pNext is NULL or a pointer to a structure extending this structure. |
| uint64_t externalFormat | externalFormat is an implementation-defined identifier for the external format. |


