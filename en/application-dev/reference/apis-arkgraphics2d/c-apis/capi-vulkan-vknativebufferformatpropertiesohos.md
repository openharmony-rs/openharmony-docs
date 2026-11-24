# VkNativeBufferFormatPropertiesOHOS

```c
typedef struct VkNativeBufferFormatPropertiesOHOS {...} VkNativeBufferFormatPropertiesOHOS
```

## Overview

Defines the format properties of a <b>OH_NativeBuffer</b>.

<!--Device-struct VkNativeBufferFormatPropertiesOHOS {...}--><!--Device-struct VkNativeBufferFormatPropertiesOHOS {...}-End-->

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
| VkFormat format | Format properties.<br><!--Device-VkFormat format--><!--Device-VkFormat format-End--> |
| uint64_t externalFormat | Externally defined format.<br><!--Device-uint64_t externalFormat--><!--Device-uint64_t externalFormat-End--> |
| VkFormatFeatureFlags formatFeatures | Features of the externally defined format.<br><!--Device-VkFormatFeatureFlags formatFeatures--><!--Device-VkFormatFeatureFlags formatFeatures-End--> |
| VkComponentMapping samplerYcbcrConversionComponents | A group of VkComponentSwizzles.<br><!--Device-VkComponentMapping samplerYcbcrConversionComponents--><!--Device-VkComponentMapping samplerYcbcrConversionComponents-End--> |
| VkSamplerYcbcrModelConversion suggestedYcbcrModel | Color model.<br><!--Device-VkSamplerYcbcrModelConversion suggestedYcbcrModel--><!--Device-VkSamplerYcbcrModelConversion suggestedYcbcrModel-End--> |
| VkSamplerYcbcrRange suggestedYcbcrRange | Color value range.<br><!--Device-VkSamplerYcbcrRange suggestedYcbcrRange--><!--Device-VkSamplerYcbcrRange suggestedYcbcrRange-End--> |
| VkChromaLocation suggestedXChromaOffset | X chrominance offset.<br><!--Device-VkChromaLocation suggestedXChromaOffset--><!--Device-VkChromaLocation suggestedXChromaOffset-End--> |
| VkChromaLocation suggestedYChromaOffset | Y chrominance offset.<br><!--Device-VkChromaLocation suggestedYChromaOffset--><!--Device-VkChromaLocation suggestedYChromaOffset-End--> |


