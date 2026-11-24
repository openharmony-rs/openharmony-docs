# StdVideoEncodeAV1PictureInfo

## Overview

<!--Device-struct StdVideoEncodeAV1PictureInfo {...}--><!--Device-struct StdVideoEncodeAV1PictureInfo {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [StdVideoEncodeAV1PictureInfoFlags](capi--stdvideoencodeav1pictureinfoflags.md) flags | <!--Device-StdVideoEncodeAV1PictureInfoFlags flags--><!--Device-StdVideoEncodeAV1PictureInfoFlags flags-End--> |
| StdVideoAV1FrameType frame_type | <!--Device-StdVideoAV1FrameType frame_type--><!--Device-StdVideoAV1FrameType frame_type-End--> |
| uint32_t frame_presentation_time | <!--Device-uint32_t frame_presentation_time--><!--Device-uint32_t frame_presentation_time-End--> |
| uint32_t current_frame_id | <!--Device-uint32_t current_frame_id--><!--Device-uint32_t current_frame_id-End--> |
| uint8_t order_hint | <!--Device-uint8_t order_hint--><!--Device-uint8_t order_hint-End--> |
| uint8_t primary_ref_frame | <!--Device-uint8_t primary_ref_frame--><!--Device-uint8_t primary_ref_frame-End--> |
| uint8_t refresh_frame_flags | <!--Device-uint8_t refresh_frame_flags--><!--Device-uint8_t refresh_frame_flags-End--> |
| uint8_t coded_denom | <!--Device-uint8_t coded_denom--><!--Device-uint8_t coded_denom-End--> |
| uint16_t render_width_minus_1 | <!--Device-uint16_t render_width_minus_1--><!--Device-uint16_t render_width_minus_1-End--> |
| uint16_t render_height_minus_1 | <!--Device-uint16_t render_height_minus_1--><!--Device-uint16_t render_height_minus_1-End--> |
| StdVideoAV1InterpolationFilter interpolation_filter | <!--Device-StdVideoAV1InterpolationFilter interpolation_filter--><!--Device-StdVideoAV1InterpolationFilter interpolation_filter-End--> |
| StdVideoAV1TxMode TxMode | <!--Device-StdVideoAV1TxMode TxMode--><!--Device-StdVideoAV1TxMode TxMode-End--> |
| uint8_t delta_q_res | <!--Device-uint8_t delta_q_res--><!--Device-uint8_t delta_q_res-End--> |
| uint8_t delta_lf_res | <!--Device-uint8_t delta_lf_res--><!--Device-uint8_t delta_lf_res-End--> |
| uint8_t ref_order_hint[STD_VIDEO_AV1_NUM_REF_FRAMES] | <!--Device-uint8_t ref_order_hint[STD_VIDEO_AV1_NUM_REF_FRAMES]--><!--Device-uint8_t ref_order_hint[STD_VIDEO_AV1_NUM_REF_FRAMES]-End--> |
| int8_t ref_frame_idx[STD_VIDEO_AV1_REFS_PER_FRAME] | <!--Device-int8_t ref_frame_idx[STD_VIDEO_AV1_REFS_PER_FRAME]--><!--Device-int8_t ref_frame_idx[STD_VIDEO_AV1_REFS_PER_FRAME]-End--> |
| uint8_t reserved1[3] | <!--Device-uint8_t reserved1[3]--><!--Device-uint8_t reserved1[3]-End--> |
| uint32_t delta_frame_id_minus_1[STD_VIDEO_AV1_REFS_PER_FRAME] | <!--Device-uint32_t delta_frame_id_minus_1[STD_VIDEO_AV1_REFS_PER_FRAME]--><!--Device-uint32_t delta_frame_id_minus_1[STD_VIDEO_AV1_REFS_PER_FRAME]-End--> |
| [const StdVideoAV1TileInfo*](capi--stdvideoav1tileinfo.md) pTileInfo | <!--Device-const StdVideoAV1TileInfo* pTileInfo--><!--Device-const StdVideoAV1TileInfo* pTileInfo-End--> |
| [const StdVideoAV1Quantization*](capi--stdvideoav1quantization.md) pQuantization | <!--Device-const StdVideoAV1Quantization* pQuantization--><!--Device-const StdVideoAV1Quantization* pQuantization-End--> |
| [const StdVideoAV1Segmentation*](capi--stdvideoav1segmentation.md) pSegmentation | <!--Device-const StdVideoAV1Segmentation* pSegmentation--><!--Device-const StdVideoAV1Segmentation* pSegmentation-End--> |
| [const StdVideoAV1LoopFilter*](capi--stdvideoav1loopfilter.md) pLoopFilter | <!--Device-const StdVideoAV1LoopFilter* pLoopFilter--><!--Device-const StdVideoAV1LoopFilter* pLoopFilter-End--> |
| [const StdVideoAV1CDEF*](capi--stdvideoav1cdef.md) pCDEF | <!--Device-const StdVideoAV1CDEF* pCDEF--><!--Device-const StdVideoAV1CDEF* pCDEF-End--> |
| [const StdVideoAV1LoopRestoration*](capi--stdvideoav1looprestoration.md) pLoopRestoration | <!--Device-const StdVideoAV1LoopRestoration* pLoopRestoration--><!--Device-const StdVideoAV1LoopRestoration* pLoopRestoration-End--> |
| [const StdVideoAV1GlobalMotion*](capi--stdvideoav1globalmotion.md) pGlobalMotion | <!--Device-const StdVideoAV1GlobalMotion* pGlobalMotion--><!--Device-const StdVideoAV1GlobalMotion* pGlobalMotion-End--> |
| [const StdVideoEncodeAV1ExtensionHeader*](capi--stdvideoencodeav1extensionheader.md) pExtensionHeader | <!--Device-const StdVideoEncodeAV1ExtensionHeader* pExtensionHeader--><!--Device-const StdVideoEncodeAV1ExtensionHeader* pExtensionHeader-End--> |
| const uint32_t* pBufferRemovalTimes | <!--Device-const uint32_t* pBufferRemovalTimes--><!--Device-const uint32_t* pBufferRemovalTimes-End--> |


