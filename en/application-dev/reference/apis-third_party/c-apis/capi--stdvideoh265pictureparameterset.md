# StdVideoH265PictureParameterSet

## Overview

<!--Device-struct StdVideoH265PictureParameterSet {...}--><!--Device-struct StdVideoH265PictureParameterSet {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [StdVideoH265PpsFlags](capi--stdvideoh265ppsflags.md) flags | <!--Device-StdVideoH265PpsFlags flags--><!--Device-StdVideoH265PpsFlags flags-End--> |
| uint8_t pps_pic_parameter_set_id | <!--Device-uint8_t pps_pic_parameter_set_id--><!--Device-uint8_t pps_pic_parameter_set_id-End--> |
| uint8_t pps_seq_parameter_set_id | <!--Device-uint8_t pps_seq_parameter_set_id--><!--Device-uint8_t pps_seq_parameter_set_id-End--> |
| uint8_t sps_video_parameter_set_id | <!--Device-uint8_t sps_video_parameter_set_id--><!--Device-uint8_t sps_video_parameter_set_id-End--> |
| uint8_t num_extra_slice_header_bits | <!--Device-uint8_t num_extra_slice_header_bits--><!--Device-uint8_t num_extra_slice_header_bits-End--> |
| uint8_t num_ref_idx_l0_default_active_minus1 | <!--Device-uint8_t num_ref_idx_l0_default_active_minus1--><!--Device-uint8_t num_ref_idx_l0_default_active_minus1-End--> |
| uint8_t num_ref_idx_l1_default_active_minus1 | <!--Device-uint8_t num_ref_idx_l1_default_active_minus1--><!--Device-uint8_t num_ref_idx_l1_default_active_minus1-End--> |
| int8_t init_qp_minus26 | <!--Device-int8_t init_qp_minus26--><!--Device-int8_t init_qp_minus26-End--> |
| uint8_t diff_cu_qp_delta_depth | <!--Device-uint8_t diff_cu_qp_delta_depth--><!--Device-uint8_t diff_cu_qp_delta_depth-End--> |
| int8_t pps_cb_qp_offset | <!--Device-int8_t pps_cb_qp_offset--><!--Device-int8_t pps_cb_qp_offset-End--> |
| int8_t pps_cr_qp_offset | <!--Device-int8_t pps_cr_qp_offset--><!--Device-int8_t pps_cr_qp_offset-End--> |
| int8_t pps_beta_offset_div2 | <!--Device-int8_t pps_beta_offset_div2--><!--Device-int8_t pps_beta_offset_div2-End--> |
| int8_t pps_tc_offset_div2 | <!--Device-int8_t pps_tc_offset_div2--><!--Device-int8_t pps_tc_offset_div2-End--> |
| uint8_t log2_parallel_merge_level_minus2 | <!--Device-uint8_t log2_parallel_merge_level_minus2--><!--Device-uint8_t log2_parallel_merge_level_minus2-End--> |
| uint8_t log2_max_transform_skip_block_size_minus2 | <!--Device-uint8_t log2_max_transform_skip_block_size_minus2--><!--Device-uint8_t log2_max_transform_skip_block_size_minus2-End--> |
| uint8_t diff_cu_chroma_qp_offset_depth | <!--Device-uint8_t diff_cu_chroma_qp_offset_depth--><!--Device-uint8_t diff_cu_chroma_qp_offset_depth-End--> |
| uint8_t chroma_qp_offset_list_len_minus1 | <!--Device-uint8_t chroma_qp_offset_list_len_minus1--><!--Device-uint8_t chroma_qp_offset_list_len_minus1-End--> |
| int8_t cb_qp_offset_list[STD_VIDEO_H265_CHROMA_QP_OFFSET_LIST_SIZE] | <!--Device-int8_t cb_qp_offset_list[STD_VIDEO_H265_CHROMA_QP_OFFSET_LIST_SIZE]--><!--Device-int8_t cb_qp_offset_list[STD_VIDEO_H265_CHROMA_QP_OFFSET_LIST_SIZE]-End--> |
| int8_t cr_qp_offset_list[STD_VIDEO_H265_CHROMA_QP_OFFSET_LIST_SIZE] | <!--Device-int8_t cr_qp_offset_list[STD_VIDEO_H265_CHROMA_QP_OFFSET_LIST_SIZE]--><!--Device-int8_t cr_qp_offset_list[STD_VIDEO_H265_CHROMA_QP_OFFSET_LIST_SIZE]-End--> |
| uint8_t log2_sao_offset_scale_luma | <!--Device-uint8_t log2_sao_offset_scale_luma--><!--Device-uint8_t log2_sao_offset_scale_luma-End--> |
| uint8_t log2_sao_offset_scale_chroma | <!--Device-uint8_t log2_sao_offset_scale_chroma--><!--Device-uint8_t log2_sao_offset_scale_chroma-End--> |
| int8_t pps_act_y_qp_offset_plus5 | <!--Device-int8_t pps_act_y_qp_offset_plus5--><!--Device-int8_t pps_act_y_qp_offset_plus5-End--> |
| int8_t pps_act_cb_qp_offset_plus5 | <!--Device-int8_t pps_act_cb_qp_offset_plus5--><!--Device-int8_t pps_act_cb_qp_offset_plus5-End--> |
| int8_t pps_act_cr_qp_offset_plus3 | <!--Device-int8_t pps_act_cr_qp_offset_plus3--><!--Device-int8_t pps_act_cr_qp_offset_plus3-End--> |
| uint8_t pps_num_palette_predictor_initializers | <!--Device-uint8_t pps_num_palette_predictor_initializers--><!--Device-uint8_t pps_num_palette_predictor_initializers-End--> |
| uint8_t luma_bit_depth_entry_minus8 | <!--Device-uint8_t luma_bit_depth_entry_minus8--><!--Device-uint8_t luma_bit_depth_entry_minus8-End--> |
| uint8_t chroma_bit_depth_entry_minus8 | <!--Device-uint8_t chroma_bit_depth_entry_minus8--><!--Device-uint8_t chroma_bit_depth_entry_minus8-End--> |
| uint8_t num_tile_columns_minus1 | <!--Device-uint8_t num_tile_columns_minus1--><!--Device-uint8_t num_tile_columns_minus1-End--> |
| uint8_t num_tile_rows_minus1 | <!--Device-uint8_t num_tile_rows_minus1--><!--Device-uint8_t num_tile_rows_minus1-End--> |
| uint8_t reserved1 | <!--Device-uint8_t reserved1--><!--Device-uint8_t reserved1-End--> |
| uint8_t reserved2 | <!--Device-uint8_t reserved2--><!--Device-uint8_t reserved2-End--> |
| uint16_t column_width_minus1[STD_VIDEO_H265_CHROMA_QP_OFFSET_TILE_COLS_LIST_SIZE] | <!--Device-uint16_t column_width_minus1[STD_VIDEO_H265_CHROMA_QP_OFFSET_TILE_COLS_LIST_SIZE]--><!--Device-uint16_t column_width_minus1[STD_VIDEO_H265_CHROMA_QP_OFFSET_TILE_COLS_LIST_SIZE]-End--> |
| uint16_t row_height_minus1[STD_VIDEO_H265_CHROMA_QP_OFFSET_TILE_ROWS_LIST_SIZE] | <!--Device-uint16_t row_height_minus1[STD_VIDEO_H265_CHROMA_QP_OFFSET_TILE_ROWS_LIST_SIZE]--><!--Device-uint16_t row_height_minus1[STD_VIDEO_H265_CHROMA_QP_OFFSET_TILE_ROWS_LIST_SIZE]-End--> |
| uint32_t reserved3 | <!--Device-uint32_t reserved3--><!--Device-uint32_t reserved3-End--> |
| [const StdVideoH265ScalingLists*](capi--stdvideoh265scalinglists.md) pScalingLists | <!--Device-const StdVideoH265ScalingLists* pScalingLists--><!--Device-const StdVideoH265ScalingLists* pScalingLists-End--> |
| [const StdVideoH265PredictorPaletteEntries*](capi--stdvideoh265predictorpaletteentries.md) pPredictorPaletteEntries | <!--Device-const StdVideoH265PredictorPaletteEntries* pPredictorPaletteEntries--><!--Device-const StdVideoH265PredictorPaletteEntries* pPredictorPaletteEntries-End--> |


