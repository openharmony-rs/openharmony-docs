# VkNativeBufferPropertiesOHOS

```c
typedef struct VkNativeBufferPropertiesOHOS {...} VkNativeBufferPropertiesOHOS
```

## Overview

Defines the properties of a <b>OH_NativeBuffer</b>.

<!--Device-struct VkNativeBufferPropertiesOHOS {...}--><!--Device-struct VkNativeBufferPropertiesOHOS {...}-End-->

**System capability**: SystemCapability.Graphic.Vulkan

**Since**: 10

**Related module**: [Vulkan](capi-arkgraphics2d-vulkan.md)

**Header file**: [vulkan_ohos.h](capi-vulkan-ohos-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| VkStructureType sType | Struct type.<br><!--Device-VkStructureType sType--><!--Device-VkStructureType sType-End--> |
| void* pNext | Pointer to the next-level struct.<br><!--Device-void* pNext--><!--Device-void* pNext-End--> |
| VkDeviceSize allocationSize | Defines the size of the occupied memory.<br><!--Device-VkDeviceSize allocationSize--><!--Device-VkDeviceSize allocationSize-End--> |
| uint32_t memoryTypeBits | Defines the memory type.<br><!--Device-uint32_t memoryTypeBits--><!--Device-uint32_t memoryTypeBits-End--> |


