# StdVideoEncodeH264WeightTable

## Overview

<!--Device-struct StdVideoEncodeH264WeightTable {...}--><!--Device-struct StdVideoEncodeH264WeightTable {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [StdVideoEncodeH264WeightTableFlags](capi--stdvideoencodeh264weighttableflags.md) flags | <!--Device-StdVideoEncodeH264WeightTableFlags flags--><!--Device-StdVideoEncodeH264WeightTableFlags flags-End--> |
| uint8_t luma_log2_weight_denom | <!--Device-uint8_t luma_log2_weight_denom--><!--Device-uint8_t luma_log2_weight_denom-End--> |
| uint8_t chroma_log2_weight_denom | <!--Device-uint8_t chroma_log2_weight_denom--><!--Device-uint8_t chroma_log2_weight_denom-End--> |
| int8_t luma_weight_l0[STD_VIDEO_H264_MAX_NUM_LIST_REF] | <!--Device-int8_t luma_weight_l0[STD_VIDEO_H264_MAX_NUM_LIST_REF]--><!--Device-int8_t luma_weight_l0[STD_VIDEO_H264_MAX_NUM_LIST_REF]-End--> |
| int8_t luma_offset_l0[STD_VIDEO_H264_MAX_NUM_LIST_REF] | <!--Device-int8_t luma_offset_l0[STD_VIDEO_H264_MAX_NUM_LIST_REF]--><!--Device-int8_t luma_offset_l0[STD_VIDEO_H264_MAX_NUM_LIST_REF]-End--> |
| int8_t chroma_weight_l0[STD_VIDEO_H264_MAX_NUM_LIST_REF][STD_VIDEO_H264_MAX_CHROMA_PLANES] | <!--Device-int8_t chroma_weight_l0[STD_VIDEO_H264_MAX_NUM_LIST_REF][STD_VIDEO_H264_MAX_CHROMA_PLANES]--><!--Device-int8_t chroma_weight_l0[STD_VIDEO_H264_MAX_NUM_LIST_REF][STD_VIDEO_H264_MAX_CHROMA_PLANES]-End--> |
| int8_t chroma_offset_l0[STD_VIDEO_H264_MAX_NUM_LIST_REF][STD_VIDEO_H264_MAX_CHROMA_PLANES] | <!--Device-int8_t chroma_offset_l0[STD_VIDEO_H264_MAX_NUM_LIST_REF][STD_VIDEO_H264_MAX_CHROMA_PLANES]--><!--Device-int8_t chroma_offset_l0[STD_VIDEO_H264_MAX_NUM_LIST_REF][STD_VIDEO_H264_MAX_CHROMA_PLANES]-End--> |
| int8_t luma_weight_l1[STD_VIDEO_H264_MAX_NUM_LIST_REF] | <!--Device-int8_t luma_weight_l1[STD_VIDEO_H264_MAX_NUM_LIST_REF]--><!--Device-int8_t luma_weight_l1[STD_VIDEO_H264_MAX_NUM_LIST_REF]-End--> |
| int8_t luma_offset_l1[STD_VIDEO_H264_MAX_NUM_LIST_REF] | <!--Device-int8_t luma_offset_l1[STD_VIDEO_H264_MAX_NUM_LIST_REF]--><!--Device-int8_t luma_offset_l1[STD_VIDEO_H264_MAX_NUM_LIST_REF]-End--> |
| int8_t chroma_weight_l1[STD_VIDEO_H264_MAX_NUM_LIST_REF][STD_VIDEO_H264_MAX_CHROMA_PLANES] | <!--Device-int8_t chroma_weight_l1[STD_VIDEO_H264_MAX_NUM_LIST_REF][STD_VIDEO_H264_MAX_CHROMA_PLANES]--><!--Device-int8_t chroma_weight_l1[STD_VIDEO_H264_MAX_NUM_LIST_REF][STD_VIDEO_H264_MAX_CHROMA_PLANES]-End--> |
| int8_t chroma_offset_l1[STD_VIDEO_H264_MAX_NUM_LIST_REF][STD_VIDEO_H264_MAX_CHROMA_PLANES] | <!--Device-int8_t chroma_offset_l1[STD_VIDEO_H264_MAX_NUM_LIST_REF][STD_VIDEO_H264_MAX_CHROMA_PLANES]--><!--Device-int8_t chroma_offset_l1[STD_VIDEO_H264_MAX_NUM_LIST_REF][STD_VIDEO_H264_MAX_CHROMA_PLANES]-End--> |


