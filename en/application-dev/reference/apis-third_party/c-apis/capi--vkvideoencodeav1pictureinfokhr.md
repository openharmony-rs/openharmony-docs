# VkVideoEncodeAV1PictureInfoKHR

## Overview

<!--Device-struct VkVideoEncodeAV1PictureInfoKHR {...}--><!--Device-struct VkVideoEncodeAV1PictureInfoKHR {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| VkStructureType sType | <!--Device-VkStructureType sType--><!--Device-VkStructureType sType-End--> |
| const void* pNext | <!--Device-const void* pNext--><!--Device-const void* pNext-End--> |
| VkVideoEncodeAV1PredictionModeKHR predictionMode | <!--Device-VkVideoEncodeAV1PredictionModeKHR predictionMode--><!--Device-VkVideoEncodeAV1PredictionModeKHR predictionMode-End--> |
| VkVideoEncodeAV1RateControlGroupKHR rateControlGroup | <!--Device-VkVideoEncodeAV1RateControlGroupKHR rateControlGroup--><!--Device-VkVideoEncodeAV1RateControlGroupKHR rateControlGroup-End--> |
| uint32_t constantQIndex | <!--Device-uint32_t constantQIndex--><!--Device-uint32_t constantQIndex-End--> |
| [const StdVideoEncodeAV1PictureInfo*](capi--stdvideoencodeav1pictureinfo.md) pStdPictureInfo | <!--Device-const StdVideoEncodeAV1PictureInfo* pStdPictureInfo--><!--Device-const StdVideoEncodeAV1PictureInfo* pStdPictureInfo-End--> |
| int32_t referenceNameSlotIndices[VK_MAX_VIDEO_AV1_REFERENCES_PER_FRAME_KHR] | <!--Device-int32_t referenceNameSlotIndices[VK_MAX_VIDEO_AV1_REFERENCES_PER_FRAME_KHR]--><!--Device-int32_t referenceNameSlotIndices[VK_MAX_VIDEO_AV1_REFERENCES_PER_FRAME_KHR]-End--> |
| VkBool32 primaryReferenceCdfOnly | <!--Device-VkBool32 primaryReferenceCdfOnly--><!--Device-VkBool32 primaryReferenceCdfOnly-End--> |
| VkBool32 generateObuExtensionHeader | <!--Device-VkBool32 generateObuExtensionHeader--><!--Device-VkBool32 generateObuExtensionHeader-End--> |


