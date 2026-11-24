# VkVideoEncodeH264PictureInfoKHR

## Overview

<!--Device-struct VkVideoEncodeH264PictureInfoKHR {...}--><!--Device-struct VkVideoEncodeH264PictureInfoKHR {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| VkStructureType sType | <!--Device-VkStructureType sType--><!--Device-VkStructureType sType-End--> |
| const void* pNext | <!--Device-const void* pNext--><!--Device-const void* pNext-End--> |
| uint32_t naluSliceEntryCount | <!--Device-uint32_t naluSliceEntryCount--><!--Device-uint32_t naluSliceEntryCount-End--> |
| [const VkVideoEncodeH264NaluSliceInfoKHR*](capi--vkvideoencodeh264nalusliceinfokhr.md) pNaluSliceEntries | <!--Device-const VkVideoEncodeH264NaluSliceInfoKHR* pNaluSliceEntries--><!--Device-const VkVideoEncodeH264NaluSliceInfoKHR* pNaluSliceEntries-End--> |
| [const StdVideoEncodeH264PictureInfo*](capi--stdvideoencodeh264pictureinfo.md) pStdPictureInfo | <!--Device-const StdVideoEncodeH264PictureInfo* pStdPictureInfo--><!--Device-const StdVideoEncodeH264PictureInfo* pStdPictureInfo-End--> |
| VkBool32 generatePrefixNalu | <!--Device-VkBool32 generatePrefixNalu--><!--Device-VkBool32 generatePrefixNalu-End--> |


