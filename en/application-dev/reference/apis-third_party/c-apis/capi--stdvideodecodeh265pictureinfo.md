# StdVideoDecodeH265PictureInfo

## Overview

<!--Device-struct StdVideoDecodeH265PictureInfo {...}--><!--Device-struct StdVideoDecodeH265PictureInfo {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [StdVideoDecodeH265PictureInfoFlags](capi--stdvideodecodeh265pictureinfoflags.md) flags | <!--Device-StdVideoDecodeH265PictureInfoFlags flags--><!--Device-StdVideoDecodeH265PictureInfoFlags flags-End--> |
| uint8_t sps_video_parameter_set_id | <!--Device-uint8_t sps_video_parameter_set_id--><!--Device-uint8_t sps_video_parameter_set_id-End--> |
| uint8_t pps_seq_parameter_set_id | <!--Device-uint8_t pps_seq_parameter_set_id--><!--Device-uint8_t pps_seq_parameter_set_id-End--> |
| uint8_t pps_pic_parameter_set_id | <!--Device-uint8_t pps_pic_parameter_set_id--><!--Device-uint8_t pps_pic_parameter_set_id-End--> |
| uint8_t NumDeltaPocsOfRefRpsIdx | <!--Device-uint8_t NumDeltaPocsOfRefRpsIdx--><!--Device-uint8_t NumDeltaPocsOfRefRpsIdx-End--> |
| int32_t PicOrderCntVal | <!--Device-int32_t PicOrderCntVal--><!--Device-int32_t PicOrderCntVal-End--> |
| uint16_t NumBitsForSTRefPicSetInSlice | <!--Device-uint16_t NumBitsForSTRefPicSetInSlice--><!--Device-uint16_t NumBitsForSTRefPicSetInSlice-End--> |
| uint16_t reserved | <!--Device-uint16_t reserved--><!--Device-uint16_t reserved-End--> |
| uint8_t RefPicSetStCurrBefore[STD_VIDEO_DECODE_H265_REF_PIC_SET_LIST_SIZE] | <!--Device-uint8_t RefPicSetStCurrBefore[STD_VIDEO_DECODE_H265_REF_PIC_SET_LIST_SIZE]--><!--Device-uint8_t RefPicSetStCurrBefore[STD_VIDEO_DECODE_H265_REF_PIC_SET_LIST_SIZE]-End--> |
| uint8_t RefPicSetStCurrAfter[STD_VIDEO_DECODE_H265_REF_PIC_SET_LIST_SIZE] | <!--Device-uint8_t RefPicSetStCurrAfter[STD_VIDEO_DECODE_H265_REF_PIC_SET_LIST_SIZE]--><!--Device-uint8_t RefPicSetStCurrAfter[STD_VIDEO_DECODE_H265_REF_PIC_SET_LIST_SIZE]-End--> |
| uint8_t RefPicSetLtCurr[STD_VIDEO_DECODE_H265_REF_PIC_SET_LIST_SIZE] | <!--Device-uint8_t RefPicSetLtCurr[STD_VIDEO_DECODE_H265_REF_PIC_SET_LIST_SIZE]--><!--Device-uint8_t RefPicSetLtCurr[STD_VIDEO_DECODE_H265_REF_PIC_SET_LIST_SIZE]-End--> |


