# StdVideoEncodeH264PictureInfo

## Overview

<!--Device-struct StdVideoEncodeH264PictureInfo {...}--><!--Device-struct StdVideoEncodeH264PictureInfo {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [StdVideoEncodeH264PictureInfoFlags](capi--stdvideoencodeh264pictureinfoflags.md) flags | <!--Device-StdVideoEncodeH264PictureInfoFlags flags--><!--Device-StdVideoEncodeH264PictureInfoFlags flags-End--> |
| uint8_t seq_parameter_set_id | <!--Device-uint8_t seq_parameter_set_id--><!--Device-uint8_t seq_parameter_set_id-End--> |
| uint8_t pic_parameter_set_id | <!--Device-uint8_t pic_parameter_set_id--><!--Device-uint8_t pic_parameter_set_id-End--> |
| uint16_t idr_pic_id | <!--Device-uint16_t idr_pic_id--><!--Device-uint16_t idr_pic_id-End--> |
| StdVideoH264PictureType primary_pic_type | <!--Device-StdVideoH264PictureType primary_pic_type--><!--Device-StdVideoH264PictureType primary_pic_type-End--> |
| uint32_t frame_num | <!--Device-uint32_t frame_num--><!--Device-uint32_t frame_num-End--> |
| int32_t PicOrderCnt | <!--Device-int32_t PicOrderCnt--><!--Device-int32_t PicOrderCnt-End--> |
| uint8_t temporal_id | <!--Device-uint8_t temporal_id--><!--Device-uint8_t temporal_id-End--> |
| uint8_t reserved1[3] | <!--Device-uint8_t reserved1[3]--><!--Device-uint8_t reserved1[3]-End--> |
| [const StdVideoEncodeH264ReferenceListsInfo*](capi--stdvideoencodeh264referencelistsinfo.md) pRefLists | <!--Device-const StdVideoEncodeH264ReferenceListsInfo* pRefLists--><!--Device-const StdVideoEncodeH264ReferenceListsInfo* pRefLists-End--> |


