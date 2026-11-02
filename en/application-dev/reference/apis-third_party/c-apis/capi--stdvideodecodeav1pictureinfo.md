# StdVideoDecodeAV1PictureInfo

## Overview

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [StdVideoDecodeAV1PictureInfoFlags](capi--stdvideodecodeav1pictureinfoflags.md) flags |  |
| StdVideoAV1FrameType frame_type |  |
| uint32_t current_frame_id |  |
| uint8_t OrderHint |  |
| uint8_t primary_ref_frame |  |
| uint8_t refresh_frame_flags |  |
| uint8_t reserved1 |  |
| StdVideoAV1InterpolationFilter interpolation_filter |  |
| StdVideoAV1TxMode TxMode |  |
| uint8_t delta_q_res |  |
| uint8_t delta_lf_res |  |
| uint8_t SkipModeFrame[STD_VIDEO_AV1_SKIP_MODE_FRAMES] |  |
| uint8_t coded_denom |  |
| uint8_t reserved2[3] |  |
| uint8_t OrderHints[STD_VIDEO_AV1_NUM_REF_FRAMES] |  |
| uint32_t expectedFrameId[STD_VIDEO_AV1_NUM_REF_FRAMES] |  |
| [const StdVideoAV1TileInfo*](capi--stdvideoav1tileinfo.md) pTileInfo |  |
| [const StdVideoAV1Quantization*](capi--stdvideoav1quantization.md) pQuantization |  |
| [const StdVideoAV1Segmentation*](capi--stdvideoav1segmentation.md) pSegmentation |  |
| [const StdVideoAV1LoopFilter*](capi--stdvideoav1loopfilter.md) pLoopFilter |  |
| [const StdVideoAV1CDEF*](capi--stdvideoav1cdef.md) pCDEF |  |
| [const StdVideoAV1LoopRestoration*](capi--stdvideoav1looprestoration.md) pLoopRestoration |  |
| [const StdVideoAV1GlobalMotion*](capi--stdvideoav1globalmotion.md) pGlobalMotion |  |
| [const StdVideoAV1FilmGrain*](capi--stdvideoav1filmgrain.md) pFilmGrain |  |


