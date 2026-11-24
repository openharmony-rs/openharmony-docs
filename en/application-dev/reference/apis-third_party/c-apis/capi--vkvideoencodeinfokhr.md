# VkVideoEncodeInfoKHR

## Overview

<!--Device-struct VkVideoEncodeInfoKHR {...}--><!--Device-struct VkVideoEncodeInfoKHR {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| VkStructureType sType | <!--Device-VkStructureType sType--><!--Device-VkStructureType sType-End--> |
| const void* pNext | <!--Device-const void* pNext--><!--Device-const void* pNext-End--> |
| VkVideoEncodeFlagsKHR flags | <!--Device-VkVideoEncodeFlagsKHR flags--><!--Device-VkVideoEncodeFlagsKHR flags-End--> |
| VkBuffer dstBuffer | <!--Device-VkBuffer dstBuffer--><!--Device-VkBuffer dstBuffer-End--> |
| VkDeviceSize dstBufferOffset | <!--Device-VkDeviceSize dstBufferOffset--><!--Device-VkDeviceSize dstBufferOffset-End--> |
| VkDeviceSize dstBufferRange | <!--Device-VkDeviceSize dstBufferRange--><!--Device-VkDeviceSize dstBufferRange-End--> |
| [VkVideoPictureResourceInfoKHR](capi--vkvideopictureresourceinfokhr.md) srcPictureResource | <!--Device-VkVideoPictureResourceInfoKHR srcPictureResource--><!--Device-VkVideoPictureResourceInfoKHR srcPictureResource-End--> |
| [const VkVideoReferenceSlotInfoKHR*](capi--vkvideoreferenceslotinfokhr.md) pSetupReferenceSlot | <!--Device-const VkVideoReferenceSlotInfoKHR* pSetupReferenceSlot--><!--Device-const VkVideoReferenceSlotInfoKHR* pSetupReferenceSlot-End--> |
| uint32_t referenceSlotCount | <!--Device-uint32_t referenceSlotCount--><!--Device-uint32_t referenceSlotCount-End--> |
| [const VkVideoReferenceSlotInfoKHR*](capi--vkvideoreferenceslotinfokhr.md) pReferenceSlots | <!--Device-const VkVideoReferenceSlotInfoKHR* pReferenceSlots--><!--Device-const VkVideoReferenceSlotInfoKHR* pReferenceSlots-End--> |
| uint32_t precedingExternallyEncodedBytes | <!--Device-uint32_t precedingExternallyEncodedBytes--><!--Device-uint32_t precedingExternallyEncodedBytes-End--> |


