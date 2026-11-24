# StdVideoAV1SequenceHeader

## Overview

<!--Device-struct StdVideoAV1SequenceHeader {...}--><!--Device-struct StdVideoAV1SequenceHeader {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [StdVideoAV1SequenceHeaderFlags](capi--stdvideoav1sequenceheaderflags.md) flags | <!--Device-StdVideoAV1SequenceHeaderFlags flags--><!--Device-StdVideoAV1SequenceHeaderFlags flags-End--> |
| StdVideoAV1Profile seq_profile | <!--Device-StdVideoAV1Profile seq_profile--><!--Device-StdVideoAV1Profile seq_profile-End--> |
| uint8_t frame_width_bits_minus_1 | <!--Device-uint8_t frame_width_bits_minus_1--><!--Device-uint8_t frame_width_bits_minus_1-End--> |
| uint8_t frame_height_bits_minus_1 | <!--Device-uint8_t frame_height_bits_minus_1--><!--Device-uint8_t frame_height_bits_minus_1-End--> |
| uint16_t max_frame_width_minus_1 | <!--Device-uint16_t max_frame_width_minus_1--><!--Device-uint16_t max_frame_width_minus_1-End--> |
| uint16_t max_frame_height_minus_1 | <!--Device-uint16_t max_frame_height_minus_1--><!--Device-uint16_t max_frame_height_minus_1-End--> |
| uint8_t delta_frame_id_length_minus_2 | <!--Device-uint8_t delta_frame_id_length_minus_2--><!--Device-uint8_t delta_frame_id_length_minus_2-End--> |
| uint8_t additional_frame_id_length_minus_1 | <!--Device-uint8_t additional_frame_id_length_minus_1--><!--Device-uint8_t additional_frame_id_length_minus_1-End--> |
| uint8_t order_hint_bits_minus_1 | <!--Device-uint8_t order_hint_bits_minus_1--><!--Device-uint8_t order_hint_bits_minus_1-End--> |
| uint8_t seq_force_integer_mv | <!--Device-uint8_t seq_force_integer_mv--><!--Device-uint8_t seq_force_integer_mv-End--> |
| uint8_t seq_force_screen_content_tools | <!--Device-uint8_t seq_force_screen_content_tools--><!--Device-uint8_t seq_force_screen_content_tools-End--> |
| uint8_t reserved1[5] | <!--Device-uint8_t reserved1[5]--><!--Device-uint8_t reserved1[5]-End--> |
| [const StdVideoAV1ColorConfig*](capi--stdvideoav1colorconfig.md) pColorConfig | <!--Device-const StdVideoAV1ColorConfig* pColorConfig--><!--Device-const StdVideoAV1ColorConfig* pColorConfig-End--> |
| [const StdVideoAV1TimingInfo*](capi--stdvideoav1timinginfo.md) pTimingInfo | <!--Device-const StdVideoAV1TimingInfo* pTimingInfo--><!--Device-const StdVideoAV1TimingInfo* pTimingInfo-End--> |


