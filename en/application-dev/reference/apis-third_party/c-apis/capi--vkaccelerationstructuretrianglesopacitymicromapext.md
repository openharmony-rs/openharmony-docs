# VkAccelerationStructureTrianglesOpacityMicromapEXT

## Overview

<!--Device-struct VkAccelerationStructureTrianglesOpacityMicromapEXT {...}--><!--Device-struct VkAccelerationStructureTrianglesOpacityMicromapEXT {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| VkStructureType sType |  |
| void* pNext |  |
| VkIndexType indexType |  |
| [VkDeviceOrHostAddressConstKHR](capi--vkdeviceorhostaddressconstkhr.md) indexBuffer |  |
| VkDeviceSize indexStride |  |
| uint32_t baseTriangle |  |
| uint32_t usageCountsCount |  |
| [const VkMicromapUsageEXT*](capi--vkmicromapusageext.md) pUsageCounts |  |
| const [VkMicromapUsageEXT](capi--vkmicromapusageext.md)* const* ppUsageCounts |  |
| VkMicromapEXT micromap |  |


