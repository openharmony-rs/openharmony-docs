# StdVideoH265HrdParameters

## Overview

<!--Device-struct StdVideoH265HrdParameters {...}--><!--Device-struct StdVideoH265HrdParameters {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [StdVideoH265HrdFlags](capi--stdvideoh265hrdflags.md) flags | <!--Device-StdVideoH265HrdFlags flags--><!--Device-StdVideoH265HrdFlags flags-End--> |
| uint8_t tick_divisor_minus2 | <!--Device-uint8_t tick_divisor_minus2--><!--Device-uint8_t tick_divisor_minus2-End--> |
| uint8_t du_cpb_removal_delay_increment_length_minus1 | <!--Device-uint8_t du_cpb_removal_delay_increment_length_minus1--><!--Device-uint8_t du_cpb_removal_delay_increment_length_minus1-End--> |
| uint8_t dpb_output_delay_du_length_minus1 | <!--Device-uint8_t dpb_output_delay_du_length_minus1--><!--Device-uint8_t dpb_output_delay_du_length_minus1-End--> |
| uint8_t bit_rate_scale | <!--Device-uint8_t bit_rate_scale--><!--Device-uint8_t bit_rate_scale-End--> |
| uint8_t cpb_size_scale | <!--Device-uint8_t cpb_size_scale--><!--Device-uint8_t cpb_size_scale-End--> |
| uint8_t cpb_size_du_scale | <!--Device-uint8_t cpb_size_du_scale--><!--Device-uint8_t cpb_size_du_scale-End--> |
| uint8_t initial_cpb_removal_delay_length_minus1 | <!--Device-uint8_t initial_cpb_removal_delay_length_minus1--><!--Device-uint8_t initial_cpb_removal_delay_length_minus1-End--> |
| uint8_t au_cpb_removal_delay_length_minus1 | <!--Device-uint8_t au_cpb_removal_delay_length_minus1--><!--Device-uint8_t au_cpb_removal_delay_length_minus1-End--> |
| uint8_t dpb_output_delay_length_minus1 | <!--Device-uint8_t dpb_output_delay_length_minus1--><!--Device-uint8_t dpb_output_delay_length_minus1-End--> |
| uint8_t cpb_cnt_minus1[STD_VIDEO_H265_SUBLAYERS_LIST_SIZE] | <!--Device-uint8_t cpb_cnt_minus1[STD_VIDEO_H265_SUBLAYERS_LIST_SIZE]--><!--Device-uint8_t cpb_cnt_minus1[STD_VIDEO_H265_SUBLAYERS_LIST_SIZE]-End--> |
| uint16_t elemental_duration_in_tc_minus1[STD_VIDEO_H265_SUBLAYERS_LIST_SIZE] | <!--Device-uint16_t elemental_duration_in_tc_minus1[STD_VIDEO_H265_SUBLAYERS_LIST_SIZE]--><!--Device-uint16_t elemental_duration_in_tc_minus1[STD_VIDEO_H265_SUBLAYERS_LIST_SIZE]-End--> |
| uint16_t reserved[3] | <!--Device-uint16_t reserved[3]--><!--Device-uint16_t reserved[3]-End--> |
| [const StdVideoH265SubLayerHrdParameters*](capi--stdvideoh265sublayerhrdparameters.md) pSubLayerHrdParametersNal | <!--Device-const StdVideoH265SubLayerHrdParameters* pSubLayerHrdParametersNal--><!--Device-const StdVideoH265SubLayerHrdParameters* pSubLayerHrdParametersNal-End--> |
| [const StdVideoH265SubLayerHrdParameters*](capi--stdvideoh265sublayerhrdparameters.md) pSubLayerHrdParametersVcl | <!--Device-const StdVideoH265SubLayerHrdParameters* pSubLayerHrdParametersVcl--><!--Device-const StdVideoH265SubLayerHrdParameters* pSubLayerHrdParametersVcl-End--> |


