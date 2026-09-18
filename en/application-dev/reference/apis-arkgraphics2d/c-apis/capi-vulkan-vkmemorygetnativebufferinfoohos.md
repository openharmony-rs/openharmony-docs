# VkMemoryGetNativeBufferInfoOHOS

```c
typedef struct VkMemoryGetNativeBufferInfoOHOS {...} VkMemoryGetNativeBufferInfoOHOS
```

## Overview

Defines a struct used to obtain an <b>OH_NativeBuffer</b> from the Vulkan memory.

**Since**: 10

**Related module**: [Vulkan](capi-vulkan.md)

**Header file**: [vulkan_ohos.h](capi-vulkan-ohos-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| VkStructureType sType | sType is a VkStructureType value identifying this structure. sType must be VK_STRUCTURE_TYPE_MEMORY_GET_NATIVE_BUFFER_INFO_OHOS. |
| const void* pNext | pNext is NULL or a pointer to a structure extending this structure. pNext must be NULL |
| VkDeviceMemory memory | memory is a valid VkDeviceMemory object from which the Open Harmony OS native buffer will be exported. memory must be a valid VkDeviceMemory handle |


