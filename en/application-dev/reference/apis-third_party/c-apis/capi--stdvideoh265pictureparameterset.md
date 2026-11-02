# StdVideoH265PictureParameterSet

## Overview

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [StdVideoH265PpsFlags](capi--stdvideoh265ppsflags.md) flags |  |
| uint8_t pps_pic_parameter_set_id |  |
| uint8_t pps_seq_parameter_set_id |  |
| uint8_t sps_video_parameter_set_id |  |
| uint8_t num_extra_slice_header_bits |  |
| uint8_t num_ref_idx_l0_default_active_minus1 |  |
| uint8_t num_ref_idx_l1_default_active_minus1 |  |
| int8_t init_qp_minus26 |  |
| uint8_t diff_cu_qp_delta_depth |  |
| int8_t pps_cb_qp_offset |  |
| int8_t pps_cr_qp_offset |  |
| int8_t pps_beta_offset_div2 |  |
| int8_t pps_tc_offset_div2 |  |
| uint8_t log2_parallel_merge_level_minus2 |  |
| uint8_t log2_max_transform_skip_block_size_minus2 |  |
| uint8_t diff_cu_chroma_qp_offset_depth |  |
| uint8_t chroma_qp_offset_list_len_minus1 |  |
| int8_t cb_qp_offset_list[STD_VIDEO_H265_CHROMA_QP_OFFSET_LIST_SIZE] |  |
| int8_t cr_qp_offset_list[STD_VIDEO_H265_CHROMA_QP_OFFSET_LIST_SIZE] |  |
| uint8_t log2_sao_offset_scale_luma |  |
| uint8_t log2_sao_offset_scale_chroma |  |
| int8_t pps_act_y_qp_offset_plus5 |  |
| int8_t pps_act_cb_qp_offset_plus5 |  |
| int8_t pps_act_cr_qp_offset_plus3 |  |
| uint8_t pps_num_palette_predictor_initializers |  |
| uint8_t luma_bit_depth_entry_minus8 |  |
| uint8_t chroma_bit_depth_entry_minus8 |  |
| uint8_t num_tile_columns_minus1 |  |
| uint8_t num_tile_rows_minus1 |  |
| uint8_t reserved1 |  |
| uint8_t reserved2 |  |
| uint16_t column_width_minus1[STD_VIDEO_H265_CHROMA_QP_OFFSET_TILE_COLS_LIST_SIZE] |  |
| uint16_t row_height_minus1[STD_VIDEO_H265_CHROMA_QP_OFFSET_TILE_ROWS_LIST_SIZE] |  |
| uint32_t reserved3 |  |
| [const StdVideoH265ScalingLists*](capi--stdvideoh265scalinglists.md) pScalingLists |  |
| [const StdVideoH265PredictorPaletteEntries*](capi--stdvideoh265predictorpaletteentries.md) pPredictorPaletteEntries |  |


