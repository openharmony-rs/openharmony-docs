# VkNativeBufferUsageOHOS

```c
typedef struct VkNativeBufferUsageOHOS {...} VkNativeBufferUsageOHOS
```

## Overview

Defines the usage of a <b>OH_NativeBuffer</b>.

<!--Device-struct VkNativeBufferUsageOHOS {...}--><!--Device-struct VkNativeBufferUsageOHOS {...}-End-->

**System capability**: SystemCapability.Graphic.Vulkan

**Since**: 10

**Related module**: [Vulkan](capi-arkgraphics2d-vulkan.md)

**Header file**: [vulkan_ohos.h](capi-vulkan-ohos-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| VkStructureType sType | Struct type is a VkStructureType value identifying this structure. sType must be VK_STRUCTURE_TYPE_NATIVE_BUFFER_USAGE_OHOS.<br><!--Device-VkStructureType sType--><!--Device-VkStructureType sType-End--> |
| void* pNext | pNext is NULL or a pointer to a structure extending this structure.<br><!--Device-void* pNext--><!--Device-void* pNext-End--> |
| uint64_t OHOSNativeBufferUsage | OHOSNativeBufferUsage returns the Open Harmony OS buffer usage flags.<br><!--Device-uint64_t OHOSNativeBufferUsage--><!--Device-uint64_t OHOSNativeBufferUsage-End--> |


