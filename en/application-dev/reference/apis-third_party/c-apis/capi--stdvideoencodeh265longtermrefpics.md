# StdVideoEncodeH265LongTermRefPics

## Overview

<!--Device-struct StdVideoEncodeH265LongTermRefPics {...}--><!--Device-struct StdVideoEncodeH265LongTermRefPics {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t num_long_term_sps | <!--Device-uint8_t num_long_term_sps--><!--Device-uint8_t num_long_term_sps-End--> |
| uint8_t num_long_term_pics | <!--Device-uint8_t num_long_term_pics--><!--Device-uint8_t num_long_term_pics-End--> |
| uint8_t lt_idx_sps[STD_VIDEO_H265_MAX_LONG_TERM_REF_PICS_SPS] | <!--Device-uint8_t lt_idx_sps[STD_VIDEO_H265_MAX_LONG_TERM_REF_PICS_SPS]--><!--Device-uint8_t lt_idx_sps[STD_VIDEO_H265_MAX_LONG_TERM_REF_PICS_SPS]-End--> |
| uint8_t poc_lsb_lt[STD_VIDEO_H265_MAX_LONG_TERM_PICS] | <!--Device-uint8_t poc_lsb_lt[STD_VIDEO_H265_MAX_LONG_TERM_PICS]--><!--Device-uint8_t poc_lsb_lt[STD_VIDEO_H265_MAX_LONG_TERM_PICS]-End--> |
| uint16_t used_by_curr_pic_lt_flag | <!--Device-uint16_t used_by_curr_pic_lt_flag--><!--Device-uint16_t used_by_curr_pic_lt_flag-End--> |
| uint8_t delta_poc_msb_present_flag[STD_VIDEO_H265_MAX_DELTA_POC] | <!--Device-uint8_t delta_poc_msb_present_flag[STD_VIDEO_H265_MAX_DELTA_POC]--><!--Device-uint8_t delta_poc_msb_present_flag[STD_VIDEO_H265_MAX_DELTA_POC]-End--> |
| uint8_t delta_poc_msb_cycle_lt[STD_VIDEO_H265_MAX_DELTA_POC] | <!--Device-uint8_t delta_poc_msb_cycle_lt[STD_VIDEO_H265_MAX_DELTA_POC]--><!--Device-uint8_t delta_poc_msb_cycle_lt[STD_VIDEO_H265_MAX_DELTA_POC]-End--> |


