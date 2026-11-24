# StdVideoAV1FilmGrain

## Overview

<!--Device-struct StdVideoAV1FilmGrain {...}--><!--Device-struct StdVideoAV1FilmGrain {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [StdVideoAV1FilmGrainFlags](capi--stdvideoav1filmgrainflags.md) flags | <!--Device-StdVideoAV1FilmGrainFlags flags--><!--Device-StdVideoAV1FilmGrainFlags flags-End--> |
| uint8_t grain_scaling_minus_8 | <!--Device-uint8_t grain_scaling_minus_8--><!--Device-uint8_t grain_scaling_minus_8-End--> |
| uint8_t ar_coeff_lag | <!--Device-uint8_t ar_coeff_lag--><!--Device-uint8_t ar_coeff_lag-End--> |
| uint8_t ar_coeff_shift_minus_6 | <!--Device-uint8_t ar_coeff_shift_minus_6--><!--Device-uint8_t ar_coeff_shift_minus_6-End--> |
| uint8_t grain_scale_shift | <!--Device-uint8_t grain_scale_shift--><!--Device-uint8_t grain_scale_shift-End--> |
| uint16_t grain_seed | <!--Device-uint16_t grain_seed--><!--Device-uint16_t grain_seed-End--> |
| uint8_t film_grain_params_ref_idx | <!--Device-uint8_t film_grain_params_ref_idx--><!--Device-uint8_t film_grain_params_ref_idx-End--> |
| uint8_t num_y_points | <!--Device-uint8_t num_y_points--><!--Device-uint8_t num_y_points-End--> |
| uint8_t point_y_value[STD_VIDEO_AV1_MAX_NUM_Y_POINTS] | <!--Device-uint8_t point_y_value[STD_VIDEO_AV1_MAX_NUM_Y_POINTS]--><!--Device-uint8_t point_y_value[STD_VIDEO_AV1_MAX_NUM_Y_POINTS]-End--> |
| uint8_t point_y_scaling[STD_VIDEO_AV1_MAX_NUM_Y_POINTS] | <!--Device-uint8_t point_y_scaling[STD_VIDEO_AV1_MAX_NUM_Y_POINTS]--><!--Device-uint8_t point_y_scaling[STD_VIDEO_AV1_MAX_NUM_Y_POINTS]-End--> |
| uint8_t num_cb_points | <!--Device-uint8_t num_cb_points--><!--Device-uint8_t num_cb_points-End--> |
| uint8_t point_cb_value[STD_VIDEO_AV1_MAX_NUM_CB_POINTS] | <!--Device-uint8_t point_cb_value[STD_VIDEO_AV1_MAX_NUM_CB_POINTS]--><!--Device-uint8_t point_cb_value[STD_VIDEO_AV1_MAX_NUM_CB_POINTS]-End--> |
| uint8_t point_cb_scaling[STD_VIDEO_AV1_MAX_NUM_CB_POINTS] | <!--Device-uint8_t point_cb_scaling[STD_VIDEO_AV1_MAX_NUM_CB_POINTS]--><!--Device-uint8_t point_cb_scaling[STD_VIDEO_AV1_MAX_NUM_CB_POINTS]-End--> |
| uint8_t num_cr_points | <!--Device-uint8_t num_cr_points--><!--Device-uint8_t num_cr_points-End--> |
| uint8_t point_cr_value[STD_VIDEO_AV1_MAX_NUM_CR_POINTS] | <!--Device-uint8_t point_cr_value[STD_VIDEO_AV1_MAX_NUM_CR_POINTS]--><!--Device-uint8_t point_cr_value[STD_VIDEO_AV1_MAX_NUM_CR_POINTS]-End--> |
| uint8_t point_cr_scaling[STD_VIDEO_AV1_MAX_NUM_CR_POINTS] | <!--Device-uint8_t point_cr_scaling[STD_VIDEO_AV1_MAX_NUM_CR_POINTS]--><!--Device-uint8_t point_cr_scaling[STD_VIDEO_AV1_MAX_NUM_CR_POINTS]-End--> |
| int8_t ar_coeffs_y_plus_128[STD_VIDEO_AV1_MAX_NUM_POS_LUMA] | <!--Device-int8_t ar_coeffs_y_plus_128[STD_VIDEO_AV1_MAX_NUM_POS_LUMA]--><!--Device-int8_t ar_coeffs_y_plus_128[STD_VIDEO_AV1_MAX_NUM_POS_LUMA]-End--> |
| int8_t ar_coeffs_cb_plus_128[STD_VIDEO_AV1_MAX_NUM_POS_CHROMA] | <!--Device-int8_t ar_coeffs_cb_plus_128[STD_VIDEO_AV1_MAX_NUM_POS_CHROMA]--><!--Device-int8_t ar_coeffs_cb_plus_128[STD_VIDEO_AV1_MAX_NUM_POS_CHROMA]-End--> |
| int8_t ar_coeffs_cr_plus_128[STD_VIDEO_AV1_MAX_NUM_POS_CHROMA] | <!--Device-int8_t ar_coeffs_cr_plus_128[STD_VIDEO_AV1_MAX_NUM_POS_CHROMA]--><!--Device-int8_t ar_coeffs_cr_plus_128[STD_VIDEO_AV1_MAX_NUM_POS_CHROMA]-End--> |
| uint8_t cb_mult | <!--Device-uint8_t cb_mult--><!--Device-uint8_t cb_mult-End--> |
| uint8_t cb_luma_mult | <!--Device-uint8_t cb_luma_mult--><!--Device-uint8_t cb_luma_mult-End--> |
| uint16_t cb_offset | <!--Device-uint16_t cb_offset--><!--Device-uint16_t cb_offset-End--> |
| uint8_t cr_mult | <!--Device-uint8_t cr_mult--><!--Device-uint8_t cr_mult-End--> |
| uint8_t cr_luma_mult | <!--Device-uint8_t cr_luma_mult--><!--Device-uint8_t cr_luma_mult-End--> |
| uint16_t cr_offset | <!--Device-uint16_t cr_offset--><!--Device-uint16_t cr_offset-End--> |


