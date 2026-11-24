# VkVideoDecodeAV1PictureInfoKHR

## Overview

<!--Device-struct VkVideoDecodeAV1PictureInfoKHR {...}--><!--Device-struct VkVideoDecodeAV1PictureInfoKHR {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| VkStructureType sType | <!--Device-VkStructureType sType--><!--Device-VkStructureType sType-End--> |
| const void* pNext | <!--Device-const void* pNext--><!--Device-const void* pNext-End--> |
| [const StdVideoDecodeAV1PictureInfo*](capi--stdvideodecodeav1pictureinfo.md) pStdPictureInfo | <!--Device-const StdVideoDecodeAV1PictureInfo* pStdPictureInfo--><!--Device-const StdVideoDecodeAV1PictureInfo* pStdPictureInfo-End--> |
| int32_t referenceNameSlotIndices[VK_MAX_VIDEO_AV1_REFERENCES_PER_FRAME_KHR] | <!--Device-int32_t referenceNameSlotIndices[VK_MAX_VIDEO_AV1_REFERENCES_PER_FRAME_KHR]--><!--Device-int32_t referenceNameSlotIndices[VK_MAX_VIDEO_AV1_REFERENCES_PER_FRAME_KHR]-End--> |
| uint32_t frameHeaderOffset | <!--Device-uint32_t frameHeaderOffset--><!--Device-uint32_t frameHeaderOffset-End--> |
| uint32_t tileCount | <!--Device-uint32_t tileCount--><!--Device-uint32_t tileCount-End--> |
| const uint32_t* pTileOffsets | <!--Device-const uint32_t* pTileOffsets--><!--Device-const uint32_t* pTileOffsets-End--> |
| const uint32_t* pTileSizes | <!--Device-const uint32_t* pTileSizes--><!--Device-const uint32_t* pTileSizes-End--> |


