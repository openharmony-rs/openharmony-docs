# StdVideoEncodeH265PictureInfo

## Overview

<!--Device-struct StdVideoEncodeH265PictureInfo {...}--><!--Device-struct StdVideoEncodeH265PictureInfo {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [StdVideoEncodeH265PictureInfoFlags](capi--stdvideoencodeh265pictureinfoflags.md) flags | <!--Device-StdVideoEncodeH265PictureInfoFlags flags--><!--Device-StdVideoEncodeH265PictureInfoFlags flags-End--> |
| StdVideoH265PictureType pic_type | <!--Device-StdVideoH265PictureType pic_type--><!--Device-StdVideoH265PictureType pic_type-End--> |
| uint8_t sps_video_parameter_set_id | <!--Device-uint8_t sps_video_parameter_set_id--><!--Device-uint8_t sps_video_parameter_set_id-End--> |
| uint8_t pps_seq_parameter_set_id | <!--Device-uint8_t pps_seq_parameter_set_id--><!--Device-uint8_t pps_seq_parameter_set_id-End--> |
| uint8_t pps_pic_parameter_set_id | <!--Device-uint8_t pps_pic_parameter_set_id--><!--Device-uint8_t pps_pic_parameter_set_id-End--> |
| uint8_t short_term_ref_pic_set_idx | <!--Device-uint8_t short_term_ref_pic_set_idx--><!--Device-uint8_t short_term_ref_pic_set_idx-End--> |
| int32_t PicOrderCntVal | <!--Device-int32_t PicOrderCntVal--><!--Device-int32_t PicOrderCntVal-End--> |
| uint8_t TemporalId | <!--Device-uint8_t TemporalId--><!--Device-uint8_t TemporalId-End--> |
| uint8_t reserved1[7] | <!--Device-uint8_t reserved1[7]--><!--Device-uint8_t reserved1[7]-End--> |
| [const StdVideoEncodeH265ReferenceListsInfo*](capi--stdvideoencodeh265referencelistsinfo.md) pRefLists | <!--Device-const StdVideoEncodeH265ReferenceListsInfo* pRefLists--><!--Device-const StdVideoEncodeH265ReferenceListsInfo* pRefLists-End--> |
| [const StdVideoH265ShortTermRefPicSet*](capi--stdvideoh265shorttermrefpicset.md) pShortTermRefPicSet | <!--Device-const StdVideoH265ShortTermRefPicSet* pShortTermRefPicSet--><!--Device-const StdVideoH265ShortTermRefPicSet* pShortTermRefPicSet-End--> |
| [const StdVideoEncodeH265LongTermRefPics*](capi--stdvideoencodeh265longtermrefpics.md) pLongTermRefPics | <!--Device-const StdVideoEncodeH265LongTermRefPics* pLongTermRefPics--><!--Device-const StdVideoEncodeH265LongTermRefPics* pLongTermRefPics-End--> |


