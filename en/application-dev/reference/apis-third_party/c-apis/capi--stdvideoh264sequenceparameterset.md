# StdVideoH264SequenceParameterSet

## Overview

<!--Device-struct StdVideoH264SequenceParameterSet {...}--><!--Device-struct StdVideoH264SequenceParameterSet {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [StdVideoH264SpsFlags](capi--stdvideoh264spsflags.md) flags | <!--Device-StdVideoH264SpsFlags flags--><!--Device-StdVideoH264SpsFlags flags-End--> |
| StdVideoH264ProfileIdc profile_idc | <!--Device-StdVideoH264ProfileIdc profile_idc--><!--Device-StdVideoH264ProfileIdc profile_idc-End--> |
| StdVideoH264LevelIdc level_idc | <!--Device-StdVideoH264LevelIdc level_idc--><!--Device-StdVideoH264LevelIdc level_idc-End--> |
| StdVideoH264ChromaFormatIdc chroma_format_idc | <!--Device-StdVideoH264ChromaFormatIdc chroma_format_idc--><!--Device-StdVideoH264ChromaFormatIdc chroma_format_idc-End--> |
| uint8_t seq_parameter_set_id | <!--Device-uint8_t seq_parameter_set_id--><!--Device-uint8_t seq_parameter_set_id-End--> |
| uint8_t bit_depth_luma_minus8 | <!--Device-uint8_t bit_depth_luma_minus8--><!--Device-uint8_t bit_depth_luma_minus8-End--> |
| uint8_t bit_depth_chroma_minus8 | <!--Device-uint8_t bit_depth_chroma_minus8--><!--Device-uint8_t bit_depth_chroma_minus8-End--> |
| uint8_t log2_max_frame_num_minus4 | <!--Device-uint8_t log2_max_frame_num_minus4--><!--Device-uint8_t log2_max_frame_num_minus4-End--> |
| StdVideoH264PocType pic_order_cnt_type | <!--Device-StdVideoH264PocType pic_order_cnt_type--><!--Device-StdVideoH264PocType pic_order_cnt_type-End--> |
| int32_t offset_for_non_ref_pic | <!--Device-int32_t offset_for_non_ref_pic--><!--Device-int32_t offset_for_non_ref_pic-End--> |
| int32_t offset_for_top_to_bottom_field | <!--Device-int32_t offset_for_top_to_bottom_field--><!--Device-int32_t offset_for_top_to_bottom_field-End--> |
| uint8_t log2_max_pic_order_cnt_lsb_minus4 | <!--Device-uint8_t log2_max_pic_order_cnt_lsb_minus4--><!--Device-uint8_t log2_max_pic_order_cnt_lsb_minus4-End--> |
| uint8_t num_ref_frames_in_pic_order_cnt_cycle | <!--Device-uint8_t num_ref_frames_in_pic_order_cnt_cycle--><!--Device-uint8_t num_ref_frames_in_pic_order_cnt_cycle-End--> |
| uint8_t max_num_ref_frames | <!--Device-uint8_t max_num_ref_frames--><!--Device-uint8_t max_num_ref_frames-End--> |
| uint8_t reserved1 | <!--Device-uint8_t reserved1--><!--Device-uint8_t reserved1-End--> |
| uint32_t pic_width_in_mbs_minus1 | <!--Device-uint32_t pic_width_in_mbs_minus1--><!--Device-uint32_t pic_width_in_mbs_minus1-End--> |
| uint32_t pic_height_in_map_units_minus1 | <!--Device-uint32_t pic_height_in_map_units_minus1--><!--Device-uint32_t pic_height_in_map_units_minus1-End--> |
| uint32_t frame_crop_left_offset | <!--Device-uint32_t frame_crop_left_offset--><!--Device-uint32_t frame_crop_left_offset-End--> |
| uint32_t frame_crop_right_offset | <!--Device-uint32_t frame_crop_right_offset--><!--Device-uint32_t frame_crop_right_offset-End--> |
| uint32_t frame_crop_top_offset | <!--Device-uint32_t frame_crop_top_offset--><!--Device-uint32_t frame_crop_top_offset-End--> |
| uint32_t frame_crop_bottom_offset | <!--Device-uint32_t frame_crop_bottom_offset--><!--Device-uint32_t frame_crop_bottom_offset-End--> |
| uint32_t reserved2 | <!--Device-uint32_t reserved2--><!--Device-uint32_t reserved2-End--> |
| const int32_t* pOffsetForRefFrame | <!--Device-const int32_t* pOffsetForRefFrame--><!--Device-const int32_t* pOffsetForRefFrame-End--> |
| [const StdVideoH264ScalingLists*](capi--stdvideoh264scalinglists.md) pScalingLists | <!--Device-const StdVideoH264ScalingLists* pScalingLists--><!--Device-const StdVideoH264ScalingLists* pScalingLists-End--> |
| [const StdVideoH264SequenceParameterSetVui*](capi--stdvideoh264sequenceparametersetvui.md) pSequenceParameterSetVui | <!--Device-const StdVideoH264SequenceParameterSetVui* pSequenceParameterSetVui--><!--Device-const StdVideoH264SequenceParameterSetVui* pSequenceParameterSetVui-End--> |


