# VkVideoSessionCreateInfoKHR

## Overview

<!--Device-struct VkVideoSessionCreateInfoKHR {...}--><!--Device-struct VkVideoSessionCreateInfoKHR {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| VkStructureType sType | <!--Device-VkStructureType sType--><!--Device-VkStructureType sType-End--> |
| const void* pNext | <!--Device-const void* pNext--><!--Device-const void* pNext-End--> |
| uint32_t queueFamilyIndex | <!--Device-uint32_t queueFamilyIndex--><!--Device-uint32_t queueFamilyIndex-End--> |
| VkVideoSessionCreateFlagsKHR flags | <!--Device-VkVideoSessionCreateFlagsKHR flags--><!--Device-VkVideoSessionCreateFlagsKHR flags-End--> |
| [const VkVideoProfileInfoKHR*](capi--vkvideoprofileinfokhr.md) pVideoProfile | <!--Device-const VkVideoProfileInfoKHR* pVideoProfile--><!--Device-const VkVideoProfileInfoKHR* pVideoProfile-End--> |
| VkFormat pictureFormat | <!--Device-VkFormat pictureFormat--><!--Device-VkFormat pictureFormat-End--> |
| [VkExtent2D](capi--vkextent2d.md) maxCodedExtent | <!--Device-VkExtent2D maxCodedExtent--><!--Device-VkExtent2D maxCodedExtent-End--> |
| VkFormat referencePictureFormat | <!--Device-VkFormat referencePictureFormat--><!--Device-VkFormat referencePictureFormat-End--> |
| uint32_t maxDpbSlots | <!--Device-uint32_t maxDpbSlots--><!--Device-uint32_t maxDpbSlots-End--> |
| uint32_t maxActiveReferencePictures | <!--Device-uint32_t maxActiveReferencePictures--><!--Device-uint32_t maxActiveReferencePictures-End--> |
| [const VkExtensionProperties*](capi--vkextensionproperties.md) pStdHeaderVersion | <!--Device-const VkExtensionProperties* pStdHeaderVersion--><!--Device-const VkExtensionProperties* pStdHeaderVersion-End--> |


