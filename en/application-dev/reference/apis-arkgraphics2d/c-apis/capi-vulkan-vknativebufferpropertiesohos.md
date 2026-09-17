# VkNativeBufferPropertiesOHOS

```c
typedef struct VkNativeBufferPropertiesOHOS {...} VkNativeBufferPropertiesOHOS
```

## Overview

Defines the properties of a <b>OH_NativeBuffer</b>.

**Since**: 10

**Related module**: [Vulkan](capi-vulkan.md)

**Header file**: [vulkan_ohos.h](capi-vulkan-ohos-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| VkStructureType sType | Struct type. |
| void* pNext | Pointer to the next-level struct. |
| VkDeviceSize allocationSize | Defines the size of the occupied memory. |
| uint32_t memoryTypeBits | Defines the memory type. |


