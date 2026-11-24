# StdVideoH264HrdParameters

## Overview

<!--Device-struct StdVideoH264HrdParameters {...}--><!--Device-struct StdVideoH264HrdParameters {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t cpb_cnt_minus1 | <!--Device-uint8_t cpb_cnt_minus1--><!--Device-uint8_t cpb_cnt_minus1-End--> |
| uint8_t bit_rate_scale | <!--Device-uint8_t bit_rate_scale--><!--Device-uint8_t bit_rate_scale-End--> |
| uint8_t cpb_size_scale | <!--Device-uint8_t cpb_size_scale--><!--Device-uint8_t cpb_size_scale-End--> |
| uint8_t reserved1 | <!--Device-uint8_t reserved1--><!--Device-uint8_t reserved1-End--> |
| uint32_t bit_rate_value_minus1[STD_VIDEO_H264_CPB_CNT_LIST_SIZE] | <!--Device-uint32_t bit_rate_value_minus1[STD_VIDEO_H264_CPB_CNT_LIST_SIZE]--><!--Device-uint32_t bit_rate_value_minus1[STD_VIDEO_H264_CPB_CNT_LIST_SIZE]-End--> |
| uint32_t cpb_size_value_minus1[STD_VIDEO_H264_CPB_CNT_LIST_SIZE] | <!--Device-uint32_t cpb_size_value_minus1[STD_VIDEO_H264_CPB_CNT_LIST_SIZE]--><!--Device-uint32_t cpb_size_value_minus1[STD_VIDEO_H264_CPB_CNT_LIST_SIZE]-End--> |
| uint8_t cbr_flag[STD_VIDEO_H264_CPB_CNT_LIST_SIZE] | <!--Device-uint8_t cbr_flag[STD_VIDEO_H264_CPB_CNT_LIST_SIZE]--><!--Device-uint8_t cbr_flag[STD_VIDEO_H264_CPB_CNT_LIST_SIZE]-End--> |
| uint32_t initial_cpb_removal_delay_length_minus1 | <!--Device-uint32_t initial_cpb_removal_delay_length_minus1--><!--Device-uint32_t initial_cpb_removal_delay_length_minus1-End--> |
| uint32_t cpb_removal_delay_length_minus1 | <!--Device-uint32_t cpb_removal_delay_length_minus1--><!--Device-uint32_t cpb_removal_delay_length_minus1-End--> |
| uint32_t dpb_output_delay_length_minus1 | <!--Device-uint32_t dpb_output_delay_length_minus1--><!--Device-uint32_t dpb_output_delay_length_minus1-End--> |
| uint32_t time_offset_length | <!--Device-uint32_t time_offset_length--><!--Device-uint32_t time_offset_length-End--> |


