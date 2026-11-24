# VkClusterAccelerationStructureBuildTriangleClusterTemplateInfoNV

## Overview

<!--Device-struct VkClusterAccelerationStructureBuildTriangleClusterTemplateInfoNV {...}--><!--Device-struct VkClusterAccelerationStructureBuildTriangleClusterTemplateInfoNV {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t clusterID | <!--Device-uint32_t clusterID--><!--Device-uint32_t clusterID-End--> |
| VkClusterAccelerationStructureClusterFlagsNV clusterFlags | <!--Device-VkClusterAccelerationStructureClusterFlagsNV clusterFlags--><!--Device-VkClusterAccelerationStructureClusterFlagsNV clusterFlags-End--> |
| uint32_t triangleCount:9 | <!--Device-uint32_t triangleCount:9--><!--Device-uint32_t triangleCount:9-End--> |
| uint32_t vertexCount:9 | <!--Device-uint32_t vertexCount:9--><!--Device-uint32_t vertexCount:9-End--> |
| uint32_t positionTruncateBitCount:6 | <!--Device-uint32_t positionTruncateBitCount:6--><!--Device-uint32_t positionTruncateBitCount:6-End--> |
| uint32_t indexType:4 | <!--Device-uint32_t indexType:4--><!--Device-uint32_t indexType:4-End--> |
| uint32_t opacityMicromapIndexType:4 | <!--Device-uint32_t opacityMicromapIndexType:4--><!--Device-uint32_t opacityMicromapIndexType:4-End--> |
| [VkClusterAccelerationStructureGeometryIndexAndGeometryFlagsNV](capi--vkclusteraccelerationstructuregeometryindexandgeometryflagsnv.md) baseGeometryIndexAndGeometryFlags | <!--Device-VkClusterAccelerationStructureGeometryIndexAndGeometryFlagsNV baseGeometryIndexAndGeometryFlags--><!--Device-VkClusterAccelerationStructureGeometryIndexAndGeometryFlagsNV baseGeometryIndexAndGeometryFlags-End--> |
| uint16_t indexBufferStride | <!--Device-uint16_t indexBufferStride--><!--Device-uint16_t indexBufferStride-End--> |
| uint16_t vertexBufferStride | <!--Device-uint16_t vertexBufferStride--><!--Device-uint16_t vertexBufferStride-End--> |
| uint16_t geometryIndexAndFlagsBufferStride | <!--Device-uint16_t geometryIndexAndFlagsBufferStride--><!--Device-uint16_t geometryIndexAndFlagsBufferStride-End--> |
| uint16_t opacityMicromapIndexBufferStride | <!--Device-uint16_t opacityMicromapIndexBufferStride--><!--Device-uint16_t opacityMicromapIndexBufferStride-End--> |
| VkDeviceAddress indexBuffer | <!--Device-VkDeviceAddress indexBuffer--><!--Device-VkDeviceAddress indexBuffer-End--> |
| VkDeviceAddress vertexBuffer | <!--Device-VkDeviceAddress vertexBuffer--><!--Device-VkDeviceAddress vertexBuffer-End--> |
| VkDeviceAddress geometryIndexAndFlagsBuffer | <!--Device-VkDeviceAddress geometryIndexAndFlagsBuffer--><!--Device-VkDeviceAddress geometryIndexAndFlagsBuffer-End--> |
| VkDeviceAddress opacityMicromapArray | <!--Device-VkDeviceAddress opacityMicromapArray--><!--Device-VkDeviceAddress opacityMicromapArray-End--> |
| VkDeviceAddress opacityMicromapIndexBuffer | <!--Device-VkDeviceAddress opacityMicromapIndexBuffer--><!--Device-VkDeviceAddress opacityMicromapIndexBuffer-End--> |
| VkDeviceAddress instantiationBoundingBoxLimit | <!--Device-VkDeviceAddress instantiationBoundingBoxLimit--><!--Device-VkDeviceAddress instantiationBoundingBoxLimit-End--> |


