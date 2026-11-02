# StdVideoH264SequenceParameterSet

## Overview

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [StdVideoH264SpsFlags](capi--stdvideoh264spsflags.md) flags |  |
| StdVideoH264ProfileIdc profile_idc |  |
| StdVideoH264LevelIdc level_idc |  |
| StdVideoH264ChromaFormatIdc chroma_format_idc |  |
| uint8_t seq_parameter_set_id |  |
| uint8_t bit_depth_luma_minus8 |  |
| uint8_t bit_depth_chroma_minus8 |  |
| uint8_t log2_max_frame_num_minus4 |  |
| StdVideoH264PocType pic_order_cnt_type |  |
| int32_t offset_for_non_ref_pic |  |
| int32_t offset_for_top_to_bottom_field |  |
| uint8_t log2_max_pic_order_cnt_lsb_minus4 |  |
| uint8_t num_ref_frames_in_pic_order_cnt_cycle |  |
| uint8_t max_num_ref_frames |  |
| uint8_t reserved1 |  |
| uint32_t pic_width_in_mbs_minus1 |  |
| uint32_t pic_height_in_map_units_minus1 |  |
| uint32_t frame_crop_left_offset |  |
| uint32_t frame_crop_right_offset |  |
| uint32_t frame_crop_top_offset |  |
| uint32_t frame_crop_bottom_offset |  |
| uint32_t reserved2 |  |
| const int32_t* pOffsetForRefFrame |  |
| [const StdVideoH264ScalingLists*](capi--stdvideoh264scalinglists.md) pScalingLists |  |
| [const StdVideoH264SequenceParameterSetVui*](capi--stdvideoh264sequenceparametersetvui.md) pSequenceParameterSetVui |  |


