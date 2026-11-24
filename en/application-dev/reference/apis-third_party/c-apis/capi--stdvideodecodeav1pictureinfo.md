# StdVideoDecodeAV1PictureInfo

## Overview

<!--Device-struct StdVideoDecodeAV1PictureInfo {...}--><!--Device-struct StdVideoDecodeAV1PictureInfo {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [StdVideoDecodeAV1PictureInfoFlags](capi--stdvideodecodeav1pictureinfoflags.md) flags | <!--Device-StdVideoDecodeAV1PictureInfoFlags flags--><!--Device-StdVideoDecodeAV1PictureInfoFlags flags-End--> |
| StdVideoAV1FrameType frame_type | <!--Device-StdVideoAV1FrameType frame_type--><!--Device-StdVideoAV1FrameType frame_type-End--> |
| uint32_t current_frame_id | <!--Device-uint32_t current_frame_id--><!--Device-uint32_t current_frame_id-End--> |
| uint8_t OrderHint | <!--Device-uint8_t OrderHint--><!--Device-uint8_t OrderHint-End--> |
| uint8_t primary_ref_frame | <!--Device-uint8_t primary_ref_frame--><!--Device-uint8_t primary_ref_frame-End--> |
| uint8_t refresh_frame_flags | <!--Device-uint8_t refresh_frame_flags--><!--Device-uint8_t refresh_frame_flags-End--> |
| uint8_t reserved1 | <!--Device-uint8_t reserved1--><!--Device-uint8_t reserved1-End--> |
| StdVideoAV1InterpolationFilter interpolation_filter | <!--Device-StdVideoAV1InterpolationFilter interpolation_filter--><!--Device-StdVideoAV1InterpolationFilter interpolation_filter-End--> |
| StdVideoAV1TxMode TxMode | <!--Device-StdVideoAV1TxMode TxMode--><!--Device-StdVideoAV1TxMode TxMode-End--> |
| uint8_t delta_q_res | <!--Device-uint8_t delta_q_res--><!--Device-uint8_t delta_q_res-End--> |
| uint8_t delta_lf_res | <!--Device-uint8_t delta_lf_res--><!--Device-uint8_t delta_lf_res-End--> |
| uint8_t SkipModeFrame[STD_VIDEO_AV1_SKIP_MODE_FRAMES] | <!--Device-uint8_t SkipModeFrame[STD_VIDEO_AV1_SKIP_MODE_FRAMES]--><!--Device-uint8_t SkipModeFrame[STD_VIDEO_AV1_SKIP_MODE_FRAMES]-End--> |
| uint8_t coded_denom | <!--Device-uint8_t coded_denom--><!--Device-uint8_t coded_denom-End--> |
| uint8_t reserved2[3] | <!--Device-uint8_t reserved2[3]--><!--Device-uint8_t reserved2[3]-End--> |
| uint8_t OrderHints[STD_VIDEO_AV1_NUM_REF_FRAMES] | <!--Device-uint8_t OrderHints[STD_VIDEO_AV1_NUM_REF_FRAMES]--><!--Device-uint8_t OrderHints[STD_VIDEO_AV1_NUM_REF_FRAMES]-End--> |
| uint32_t expectedFrameId[STD_VIDEO_AV1_NUM_REF_FRAMES] | <!--Device-uint32_t expectedFrameId[STD_VIDEO_AV1_NUM_REF_FRAMES]--><!--Device-uint32_t expectedFrameId[STD_VIDEO_AV1_NUM_REF_FRAMES]-End--> |
| [const StdVideoAV1TileInfo*](capi--stdvideoav1tileinfo.md) pTileInfo | <!--Device-const StdVideoAV1TileInfo* pTileInfo--><!--Device-const StdVideoAV1TileInfo* pTileInfo-End--> |
| [const StdVideoAV1Quantization*](capi--stdvideoav1quantization.md) pQuantization | <!--Device-const StdVideoAV1Quantization* pQuantization--><!--Device-const StdVideoAV1Quantization* pQuantization-End--> |
| [const StdVideoAV1Segmentation*](capi--stdvideoav1segmentation.md) pSegmentation | <!--Device-const StdVideoAV1Segmentation* pSegmentation--><!--Device-const StdVideoAV1Segmentation* pSegmentation-End--> |
| [const StdVideoAV1LoopFilter*](capi--stdvideoav1loopfilter.md) pLoopFilter | <!--Device-const StdVideoAV1LoopFilter* pLoopFilter--><!--Device-const StdVideoAV1LoopFilter* pLoopFilter-End--> |
| [const StdVideoAV1CDEF*](capi--stdvideoav1cdef.md) pCDEF | <!--Device-const StdVideoAV1CDEF* pCDEF--><!--Device-const StdVideoAV1CDEF* pCDEF-End--> |
| [const StdVideoAV1LoopRestoration*](capi--stdvideoav1looprestoration.md) pLoopRestoration | <!--Device-const StdVideoAV1LoopRestoration* pLoopRestoration--><!--Device-const StdVideoAV1LoopRestoration* pLoopRestoration-End--> |
| [const StdVideoAV1GlobalMotion*](capi--stdvideoav1globalmotion.md) pGlobalMotion | <!--Device-const StdVideoAV1GlobalMotion* pGlobalMotion--><!--Device-const StdVideoAV1GlobalMotion* pGlobalMotion-End--> |
| [const StdVideoAV1FilmGrain*](capi--stdvideoav1filmgrain.md) pFilmGrain | <!--Device-const StdVideoAV1FilmGrain* pFilmGrain--><!--Device-const StdVideoAV1FilmGrain* pFilmGrain-End--> |


