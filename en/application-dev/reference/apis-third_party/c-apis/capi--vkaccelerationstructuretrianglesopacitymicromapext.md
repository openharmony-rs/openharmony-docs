# VkAccelerationStructureTrianglesOpacityMicromapEXT

## Overview

<!--Device-struct VkAccelerationStructureTrianglesOpacityMicromapEXT {...}--><!--Device-struct VkAccelerationStructureTrianglesOpacityMicromapEXT {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| VkStructureType sType | <!--Device-VkStructureType sType--><!--Device-VkStructureType sType-End--> |
| void* pNext | <!--Device-void* pNext--><!--Device-void* pNext-End--> |
| VkIndexType indexType | <!--Device-VkIndexType indexType--><!--Device-VkIndexType indexType-End--> |
| [VkDeviceOrHostAddressConstKHR](capi--vkdeviceorhostaddressconstkhr.md) indexBuffer | <!--Device-VkDeviceOrHostAddressConstKHR indexBuffer--><!--Device-VkDeviceOrHostAddressConstKHR indexBuffer-End--> |
| VkDeviceSize indexStride | <!--Device-VkDeviceSize indexStride--><!--Device-VkDeviceSize indexStride-End--> |
| uint32_t baseTriangle | <!--Device-uint32_t baseTriangle--><!--Device-uint32_t baseTriangle-End--> |
| uint32_t usageCountsCount | <!--Device-uint32_t usageCountsCount--><!--Device-uint32_t usageCountsCount-End--> |
| [const VkMicromapUsageEXT*](capi--vkmicromapusageext.md) pUsageCounts | <!--Device-const VkMicromapUsageEXT* pUsageCounts--><!--Device-const VkMicromapUsageEXT* pUsageCounts-End--> |
| const [VkMicromapUsageEXT](capi--vkmicromapusageext.md)* const* ppUsageCounts | <!--Device-const VkMicromapUsageEXT* const* ppUsageCounts--><!--Device-const VkMicromapUsageEXT* const* ppUsageCounts-End--> |
| VkMicromapEXT micromap | <!--Device-VkMicromapEXT micromap--><!--Device-VkMicromapEXT micromap-End--> |


