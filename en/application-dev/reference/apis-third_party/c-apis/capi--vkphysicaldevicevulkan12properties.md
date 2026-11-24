# VkPhysicalDeviceVulkan12Properties

## Overview

<!--Device-struct VkPhysicalDeviceVulkan12Properties {...}--><!--Device-struct VkPhysicalDeviceVulkan12Properties {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| VkStructureType sType | <!--Device-VkStructureType sType--><!--Device-VkStructureType sType-End--> |
| void* pNext | <!--Device-void* pNext--><!--Device-void* pNext-End--> |
| VkDriverId driverID | <!--Device-VkDriverId driverID--><!--Device-VkDriverId driverID-End--> |
| char driverName[VK_MAX_DRIVER_NAME_SIZE] | <!--Device-char driverName[VK_MAX_DRIVER_NAME_SIZE]--><!--Device-char driverName[VK_MAX_DRIVER_NAME_SIZE]-End--> |
| char driverInfo[VK_MAX_DRIVER_INFO_SIZE] | <!--Device-char driverInfo[VK_MAX_DRIVER_INFO_SIZE]--><!--Device-char driverInfo[VK_MAX_DRIVER_INFO_SIZE]-End--> |
| [VkConformanceVersion](capi--vkconformanceversion.md) conformanceVersion | <!--Device-VkConformanceVersion conformanceVersion--><!--Device-VkConformanceVersion conformanceVersion-End--> |
| VkShaderFloatControlsIndependence denormBehaviorIndependence | <!--Device-VkShaderFloatControlsIndependence denormBehaviorIndependence--><!--Device-VkShaderFloatControlsIndependence denormBehaviorIndependence-End--> |
| VkShaderFloatControlsIndependence roundingModeIndependence | <!--Device-VkShaderFloatControlsIndependence roundingModeIndependence--><!--Device-VkShaderFloatControlsIndependence roundingModeIndependence-End--> |
| VkBool32 shaderSignedZeroInfNanPreserveFloat16 | <!--Device-VkBool32 shaderSignedZeroInfNanPreserveFloat16--><!--Device-VkBool32 shaderSignedZeroInfNanPreserveFloat16-End--> |
| VkBool32 shaderSignedZeroInfNanPreserveFloat32 | <!--Device-VkBool32 shaderSignedZeroInfNanPreserveFloat32--><!--Device-VkBool32 shaderSignedZeroInfNanPreserveFloat32-End--> |
| VkBool32 shaderSignedZeroInfNanPreserveFloat64 | <!--Device-VkBool32 shaderSignedZeroInfNanPreserveFloat64--><!--Device-VkBool32 shaderSignedZeroInfNanPreserveFloat64-End--> |
| VkBool32 shaderDenormPreserveFloat16 | <!--Device-VkBool32 shaderDenormPreserveFloat16--><!--Device-VkBool32 shaderDenormPreserveFloat16-End--> |
| VkBool32 shaderDenormPreserveFloat32 | <!--Device-VkBool32 shaderDenormPreserveFloat32--><!--Device-VkBool32 shaderDenormPreserveFloat32-End--> |
| VkBool32 shaderDenormPreserveFloat64 | <!--Device-VkBool32 shaderDenormPreserveFloat64--><!--Device-VkBool32 shaderDenormPreserveFloat64-End--> |
| VkBool32 shaderDenormFlushToZeroFloat16 | <!--Device-VkBool32 shaderDenormFlushToZeroFloat16--><!--Device-VkBool32 shaderDenormFlushToZeroFloat16-End--> |
| VkBool32 shaderDenormFlushToZeroFloat32 | <!--Device-VkBool32 shaderDenormFlushToZeroFloat32--><!--Device-VkBool32 shaderDenormFlushToZeroFloat32-End--> |
| VkBool32 shaderDenormFlushToZeroFloat64 | <!--Device-VkBool32 shaderDenormFlushToZeroFloat64--><!--Device-VkBool32 shaderDenormFlushToZeroFloat64-End--> |
| VkBool32 shaderRoundingModeRTEFloat16 | <!--Device-VkBool32 shaderRoundingModeRTEFloat16--><!--Device-VkBool32 shaderRoundingModeRTEFloat16-End--> |
| VkBool32 shaderRoundingModeRTEFloat32 | <!--Device-VkBool32 shaderRoundingModeRTEFloat32--><!--Device-VkBool32 shaderRoundingModeRTEFloat32-End--> |
| VkBool32 shaderRoundingModeRTEFloat64 | <!--Device-VkBool32 shaderRoundingModeRTEFloat64--><!--Device-VkBool32 shaderRoundingModeRTEFloat64-End--> |
| VkBool32 shaderRoundingModeRTZFloat16 | <!--Device-VkBool32 shaderRoundingModeRTZFloat16--><!--Device-VkBool32 shaderRoundingModeRTZFloat16-End--> |
| VkBool32 shaderRoundingModeRTZFloat32 | <!--Device-VkBool32 shaderRoundingModeRTZFloat32--><!--Device-VkBool32 shaderRoundingModeRTZFloat32-End--> |
| VkBool32 shaderRoundingModeRTZFloat64 | <!--Device-VkBool32 shaderRoundingModeRTZFloat64--><!--Device-VkBool32 shaderRoundingModeRTZFloat64-End--> |
| uint32_t maxUpdateAfterBindDescriptorsInAllPools | <!--Device-uint32_t maxUpdateAfterBindDescriptorsInAllPools--><!--Device-uint32_t maxUpdateAfterBindDescriptorsInAllPools-End--> |
| VkBool32 shaderUniformBufferArrayNonUniformIndexingNative | <!--Device-VkBool32 shaderUniformBufferArrayNonUniformIndexingNative--><!--Device-VkBool32 shaderUniformBufferArrayNonUniformIndexingNative-End--> |
| VkBool32 shaderSampledImageArrayNonUniformIndexingNative | <!--Device-VkBool32 shaderSampledImageArrayNonUniformIndexingNative--><!--Device-VkBool32 shaderSampledImageArrayNonUniformIndexingNative-End--> |
| VkBool32 shaderStorageBufferArrayNonUniformIndexingNative | <!--Device-VkBool32 shaderStorageBufferArrayNonUniformIndexingNative--><!--Device-VkBool32 shaderStorageBufferArrayNonUniformIndexingNative-End--> |
| VkBool32 shaderStorageImageArrayNonUniformIndexingNative | <!--Device-VkBool32 shaderStorageImageArrayNonUniformIndexingNative--><!--Device-VkBool32 shaderStorageImageArrayNonUniformIndexingNative-End--> |
| VkBool32 shaderInputAttachmentArrayNonUniformIndexingNative | <!--Device-VkBool32 shaderInputAttachmentArrayNonUniformIndexingNative--><!--Device-VkBool32 shaderInputAttachmentArrayNonUniformIndexingNative-End--> |
| VkBool32 robustBufferAccessUpdateAfterBind | <!--Device-VkBool32 robustBufferAccessUpdateAfterBind--><!--Device-VkBool32 robustBufferAccessUpdateAfterBind-End--> |
| VkBool32 quadDivergentImplicitLod | <!--Device-VkBool32 quadDivergentImplicitLod--><!--Device-VkBool32 quadDivergentImplicitLod-End--> |
| uint32_t maxPerStageDescriptorUpdateAfterBindSamplers | <!--Device-uint32_t maxPerStageDescriptorUpdateAfterBindSamplers--><!--Device-uint32_t maxPerStageDescriptorUpdateAfterBindSamplers-End--> |
| uint32_t maxPerStageDescriptorUpdateAfterBindUniformBuffers | <!--Device-uint32_t maxPerStageDescriptorUpdateAfterBindUniformBuffers--><!--Device-uint32_t maxPerStageDescriptorUpdateAfterBindUniformBuffers-End--> |
| uint32_t maxPerStageDescriptorUpdateAfterBindStorageBuffers | <!--Device-uint32_t maxPerStageDescriptorUpdateAfterBindStorageBuffers--><!--Device-uint32_t maxPerStageDescriptorUpdateAfterBindStorageBuffers-End--> |
| uint32_t maxPerStageDescriptorUpdateAfterBindSampledImages | <!--Device-uint32_t maxPerStageDescriptorUpdateAfterBindSampledImages--><!--Device-uint32_t maxPerStageDescriptorUpdateAfterBindSampledImages-End--> |
| uint32_t maxPerStageDescriptorUpdateAfterBindStorageImages | <!--Device-uint32_t maxPerStageDescriptorUpdateAfterBindStorageImages--><!--Device-uint32_t maxPerStageDescriptorUpdateAfterBindStorageImages-End--> |
| uint32_t maxPerStageDescriptorUpdateAfterBindInputAttachments | <!--Device-uint32_t maxPerStageDescriptorUpdateAfterBindInputAttachments--><!--Device-uint32_t maxPerStageDescriptorUpdateAfterBindInputAttachments-End--> |
| uint32_t maxPerStageUpdateAfterBindResources | <!--Device-uint32_t maxPerStageUpdateAfterBindResources--><!--Device-uint32_t maxPerStageUpdateAfterBindResources-End--> |
| uint32_t maxDescriptorSetUpdateAfterBindSamplers | <!--Device-uint32_t maxDescriptorSetUpdateAfterBindSamplers--><!--Device-uint32_t maxDescriptorSetUpdateAfterBindSamplers-End--> |
| uint32_t maxDescriptorSetUpdateAfterBindUniformBuffers | <!--Device-uint32_t maxDescriptorSetUpdateAfterBindUniformBuffers--><!--Device-uint32_t maxDescriptorSetUpdateAfterBindUniformBuffers-End--> |
| uint32_t maxDescriptorSetUpdateAfterBindUniformBuffersDynamic | <!--Device-uint32_t maxDescriptorSetUpdateAfterBindUniformBuffersDynamic--><!--Device-uint32_t maxDescriptorSetUpdateAfterBindUniformBuffersDynamic-End--> |
| uint32_t maxDescriptorSetUpdateAfterBindStorageBuffers | <!--Device-uint32_t maxDescriptorSetUpdateAfterBindStorageBuffers--><!--Device-uint32_t maxDescriptorSetUpdateAfterBindStorageBuffers-End--> |
| uint32_t maxDescriptorSetUpdateAfterBindStorageBuffersDynamic | <!--Device-uint32_t maxDescriptorSetUpdateAfterBindStorageBuffersDynamic--><!--Device-uint32_t maxDescriptorSetUpdateAfterBindStorageBuffersDynamic-End--> |
| uint32_t maxDescriptorSetUpdateAfterBindSampledImages | <!--Device-uint32_t maxDescriptorSetUpdateAfterBindSampledImages--><!--Device-uint32_t maxDescriptorSetUpdateAfterBindSampledImages-End--> |
| uint32_t maxDescriptorSetUpdateAfterBindStorageImages | <!--Device-uint32_t maxDescriptorSetUpdateAfterBindStorageImages--><!--Device-uint32_t maxDescriptorSetUpdateAfterBindStorageImages-End--> |
| uint32_t maxDescriptorSetUpdateAfterBindInputAttachments | <!--Device-uint32_t maxDescriptorSetUpdateAfterBindInputAttachments--><!--Device-uint32_t maxDescriptorSetUpdateAfterBindInputAttachments-End--> |
| VkResolveModeFlags supportedDepthResolveModes | <!--Device-VkResolveModeFlags supportedDepthResolveModes--><!--Device-VkResolveModeFlags supportedDepthResolveModes-End--> |
| VkResolveModeFlags supportedStencilResolveModes | <!--Device-VkResolveModeFlags supportedStencilResolveModes--><!--Device-VkResolveModeFlags supportedStencilResolveModes-End--> |
| VkBool32 independentResolveNone | <!--Device-VkBool32 independentResolveNone--><!--Device-VkBool32 independentResolveNone-End--> |
| VkBool32 independentResolve | <!--Device-VkBool32 independentResolve--><!--Device-VkBool32 independentResolve-End--> |
| VkBool32 filterMinmaxSingleComponentFormats | <!--Device-VkBool32 filterMinmaxSingleComponentFormats--><!--Device-VkBool32 filterMinmaxSingleComponentFormats-End--> |
| VkBool32 filterMinmaxImageComponentMapping | <!--Device-VkBool32 filterMinmaxImageComponentMapping--><!--Device-VkBool32 filterMinmaxImageComponentMapping-End--> |
| uint64_t maxTimelineSemaphoreValueDifference | <!--Device-uint64_t maxTimelineSemaphoreValueDifference--><!--Device-uint64_t maxTimelineSemaphoreValueDifference-End--> |
| VkSampleCountFlags framebufferIntegerColorSampleCounts | <!--Device-VkSampleCountFlags framebufferIntegerColorSampleCounts--><!--Device-VkSampleCountFlags framebufferIntegerColorSampleCounts-End--> |


