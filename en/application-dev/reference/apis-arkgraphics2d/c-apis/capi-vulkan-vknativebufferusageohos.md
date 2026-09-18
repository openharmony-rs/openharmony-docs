# VkNativeBufferUsageOHOS

```c
typedef struct VkNativeBufferUsageOHOS {...} VkNativeBufferUsageOHOS
```

## Overview

Defines the usage of a <b>OH_NativeBuffer</b>.

**Since**: 10

**Related module**: [Vulkan](capi-vulkan.md)

**Header file**: [vulkan_ohos.h](capi-vulkan-ohos-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| VkStructureType sType | Struct type is a VkStructureType value identifying this structure. sType must be VK_STRUCTURE_TYPE_NATIVE_BUFFER_USAGE_OHOS. |
| void* pNext | pNext is NULL or a pointer to a structure extending this structure. |
| uint64_t OHOSNativeBufferUsage | OHOSNativeBufferUsage returns the Open Harmony OS buffer usage flags. |


