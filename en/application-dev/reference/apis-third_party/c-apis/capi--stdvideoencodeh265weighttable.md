# StdVideoEncodeH265WeightTable

## Overview

<!--Device-struct StdVideoEncodeH265WeightTable {...}--><!--Device-struct StdVideoEncodeH265WeightTable {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [StdVideoEncodeH265WeightTableFlags](capi--stdvideoencodeh265weighttableflags.md) flags | <!--Device-StdVideoEncodeH265WeightTableFlags flags--><!--Device-StdVideoEncodeH265WeightTableFlags flags-End--> |
| uint8_t luma_log2_weight_denom | <!--Device-uint8_t luma_log2_weight_denom--><!--Device-uint8_t luma_log2_weight_denom-End--> |
| int8_t delta_chroma_log2_weight_denom | <!--Device-int8_t delta_chroma_log2_weight_denom--><!--Device-int8_t delta_chroma_log2_weight_denom-End--> |
| int8_t delta_luma_weight_l0[STD_VIDEO_H265_MAX_NUM_LIST_REF] | <!--Device-int8_t delta_luma_weight_l0[STD_VIDEO_H265_MAX_NUM_LIST_REF]--><!--Device-int8_t delta_luma_weight_l0[STD_VIDEO_H265_MAX_NUM_LIST_REF]-End--> |
| int8_t luma_offset_l0[STD_VIDEO_H265_MAX_NUM_LIST_REF] | <!--Device-int8_t luma_offset_l0[STD_VIDEO_H265_MAX_NUM_LIST_REF]--><!--Device-int8_t luma_offset_l0[STD_VIDEO_H265_MAX_NUM_LIST_REF]-End--> |
| int8_t delta_chroma_weight_l0[STD_VIDEO_H265_MAX_NUM_LIST_REF][STD_VIDEO_H265_MAX_CHROMA_PLANES] | <!--Device-int8_t delta_chroma_weight_l0[STD_VIDEO_H265_MAX_NUM_LIST_REF][STD_VIDEO_H265_MAX_CHROMA_PLANES]--><!--Device-int8_t delta_chroma_weight_l0[STD_VIDEO_H265_MAX_NUM_LIST_REF][STD_VIDEO_H265_MAX_CHROMA_PLANES]-End--> |
| int8_t delta_chroma_offset_l0[STD_VIDEO_H265_MAX_NUM_LIST_REF][STD_VIDEO_H265_MAX_CHROMA_PLANES] | <!--Device-int8_t delta_chroma_offset_l0[STD_VIDEO_H265_MAX_NUM_LIST_REF][STD_VIDEO_H265_MAX_CHROMA_PLANES]--><!--Device-int8_t delta_chroma_offset_l0[STD_VIDEO_H265_MAX_NUM_LIST_REF][STD_VIDEO_H265_MAX_CHROMA_PLANES]-End--> |
| int8_t delta_luma_weight_l1[STD_VIDEO_H265_MAX_NUM_LIST_REF] | <!--Device-int8_t delta_luma_weight_l1[STD_VIDEO_H265_MAX_NUM_LIST_REF]--><!--Device-int8_t delta_luma_weight_l1[STD_VIDEO_H265_MAX_NUM_LIST_REF]-End--> |
| int8_t luma_offset_l1[STD_VIDEO_H265_MAX_NUM_LIST_REF] | <!--Device-int8_t luma_offset_l1[STD_VIDEO_H265_MAX_NUM_LIST_REF]--><!--Device-int8_t luma_offset_l1[STD_VIDEO_H265_MAX_NUM_LIST_REF]-End--> |
| int8_t delta_chroma_weight_l1[STD_VIDEO_H265_MAX_NUM_LIST_REF][STD_VIDEO_H265_MAX_CHROMA_PLANES] | <!--Device-int8_t delta_chroma_weight_l1[STD_VIDEO_H265_MAX_NUM_LIST_REF][STD_VIDEO_H265_MAX_CHROMA_PLANES]--><!--Device-int8_t delta_chroma_weight_l1[STD_VIDEO_H265_MAX_NUM_LIST_REF][STD_VIDEO_H265_MAX_CHROMA_PLANES]-End--> |
| int8_t delta_chroma_offset_l1[STD_VIDEO_H265_MAX_NUM_LIST_REF][STD_VIDEO_H265_MAX_CHROMA_PLANES] | <!--Device-int8_t delta_chroma_offset_l1[STD_VIDEO_H265_MAX_NUM_LIST_REF][STD_VIDEO_H265_MAX_CHROMA_PLANES]--><!--Device-int8_t delta_chroma_offset_l1[STD_VIDEO_H265_MAX_NUM_LIST_REF][STD_VIDEO_H265_MAX_CHROMA_PLANES]-End--> |


