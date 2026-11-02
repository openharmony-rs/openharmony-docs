# StdVideoH265HrdParameters

## Overview

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [StdVideoH265HrdFlags](capi--stdvideoh265hrdflags.md) flags |  |
| uint8_t tick_divisor_minus2 |  |
| uint8_t du_cpb_removal_delay_increment_length_minus1 |  |
| uint8_t dpb_output_delay_du_length_minus1 |  |
| uint8_t bit_rate_scale |  |
| uint8_t cpb_size_scale |  |
| uint8_t cpb_size_du_scale |  |
| uint8_t initial_cpb_removal_delay_length_minus1 |  |
| uint8_t au_cpb_removal_delay_length_minus1 |  |
| uint8_t dpb_output_delay_length_minus1 |  |
| uint8_t cpb_cnt_minus1[STD_VIDEO_H265_SUBLAYERS_LIST_SIZE] |  |
| uint16_t elemental_duration_in_tc_minus1[STD_VIDEO_H265_SUBLAYERS_LIST_SIZE] |  |
| uint16_t reserved[3] |  |
| [const StdVideoH265SubLayerHrdParameters*](capi--stdvideoh265sublayerhrdparameters.md) pSubLayerHrdParametersNal |  |
| [const StdVideoH265SubLayerHrdParameters*](capi--stdvideoh265sublayerhrdparameters.md) pSubLayerHrdParametersVcl |  |


