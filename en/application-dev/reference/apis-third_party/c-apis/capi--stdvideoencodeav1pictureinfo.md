# StdVideoEncodeAV1PictureInfo

## Overview

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [StdVideoEncodeAV1PictureInfoFlags](capi--stdvideoencodeav1pictureinfoflags.md) flags |  |
| StdVideoAV1FrameType frame_type |  |
| uint32_t frame_presentation_time |  |
| uint32_t current_frame_id |  |
| uint8_t order_hint |  |
| uint8_t primary_ref_frame |  |
| uint8_t refresh_frame_flags |  |
| uint8_t coded_denom |  |
| uint16_t render_width_minus_1 |  |
| uint16_t render_height_minus_1 |  |
| StdVideoAV1InterpolationFilter interpolation_filter |  |
| StdVideoAV1TxMode TxMode |  |
| uint8_t delta_q_res |  |
| uint8_t delta_lf_res |  |
| uint8_t ref_order_hint[STD_VIDEO_AV1_NUM_REF_FRAMES] |  |
| int8_t ref_frame_idx[STD_VIDEO_AV1_REFS_PER_FRAME] |  |
| uint8_t reserved1[3] |  |
| uint32_t delta_frame_id_minus_1[STD_VIDEO_AV1_REFS_PER_FRAME] |  |
| [const StdVideoAV1TileInfo*](capi--stdvideoav1tileinfo.md) pTileInfo |  |
| [const StdVideoAV1Quantization*](capi--stdvideoav1quantization.md) pQuantization |  |
| [const StdVideoAV1Segmentation*](capi--stdvideoav1segmentation.md) pSegmentation |  |
| [const StdVideoAV1LoopFilter*](capi--stdvideoav1loopfilter.md) pLoopFilter |  |
| [const StdVideoAV1CDEF*](capi--stdvideoav1cdef.md) pCDEF |  |
| [const StdVideoAV1LoopRestoration*](capi--stdvideoav1looprestoration.md) pLoopRestoration |  |
| [const StdVideoAV1GlobalMotion*](capi--stdvideoav1globalmotion.md) pGlobalMotion |  |
| [const StdVideoEncodeAV1ExtensionHeader*](capi--stdvideoencodeav1extensionheader.md) pExtensionHeader |  |
| const uint32_t* pBufferRemovalTimes |  |


