# VkClusterAccelerationStructureBuildTriangleClusterInfoNV

## Overview

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t clusterID |  |
| VkClusterAccelerationStructureClusterFlagsNV clusterFlags |  |
| uint32_t triangleCount:9 |  |
| uint32_t vertexCount:9 |  |
| uint32_t positionTruncateBitCount:6 |  |
| uint32_t indexType:4 |  |
| uint32_t opacityMicromapIndexType:4 |  |
| [VkClusterAccelerationStructureGeometryIndexAndGeometryFlagsNV](capi--vkclusteraccelerationstructuregeometryindexandgeometryflagsnv.md) baseGeometryIndexAndGeometryFlags |  |
| uint16_t indexBufferStride |  |
| uint16_t vertexBufferStride |  |
| uint16_t geometryIndexAndFlagsBufferStride |  |
| uint16_t opacityMicromapIndexBufferStride |  |
| VkDeviceAddress indexBuffer |  |
| VkDeviceAddress vertexBuffer |  |
| VkDeviceAddress geometryIndexAndFlagsBuffer |  |
| VkDeviceAddress opacityMicromapArray |  |
| VkDeviceAddress opacityMicromapIndexBuffer |  |


