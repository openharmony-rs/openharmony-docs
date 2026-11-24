# StdVideoEncodeH265SliceSegmentHeader

## Overview

<!--Device-struct StdVideoEncodeH265SliceSegmentHeader {...}--><!--Device-struct StdVideoEncodeH265SliceSegmentHeader {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [StdVideoEncodeH265SliceSegmentHeaderFlags](capi--stdvideoencodeh265slicesegmentheaderflags.md) flags | <!--Device-StdVideoEncodeH265SliceSegmentHeaderFlags flags--><!--Device-StdVideoEncodeH265SliceSegmentHeaderFlags flags-End--> |
| StdVideoH265SliceType slice_type | <!--Device-StdVideoH265SliceType slice_type--><!--Device-StdVideoH265SliceType slice_type-End--> |
| uint32_t slice_segment_address | <!--Device-uint32_t slice_segment_address--><!--Device-uint32_t slice_segment_address-End--> |
| uint8_t collocated_ref_idx | <!--Device-uint8_t collocated_ref_idx--><!--Device-uint8_t collocated_ref_idx-End--> |
| uint8_t MaxNumMergeCand | <!--Device-uint8_t MaxNumMergeCand--><!--Device-uint8_t MaxNumMergeCand-End--> |
| int8_t slice_cb_qp_offset | <!--Device-int8_t slice_cb_qp_offset--><!--Device-int8_t slice_cb_qp_offset-End--> |
| int8_t slice_cr_qp_offset | <!--Device-int8_t slice_cr_qp_offset--><!--Device-int8_t slice_cr_qp_offset-End--> |
| int8_t slice_beta_offset_div2 | <!--Device-int8_t slice_beta_offset_div2--><!--Device-int8_t slice_beta_offset_div2-End--> |
| int8_t slice_tc_offset_div2 | <!--Device-int8_t slice_tc_offset_div2--><!--Device-int8_t slice_tc_offset_div2-End--> |
| int8_t slice_act_y_qp_offset | <!--Device-int8_t slice_act_y_qp_offset--><!--Device-int8_t slice_act_y_qp_offset-End--> |
| int8_t slice_act_cb_qp_offset | <!--Device-int8_t slice_act_cb_qp_offset--><!--Device-int8_t slice_act_cb_qp_offset-End--> |
| int8_t slice_act_cr_qp_offset | <!--Device-int8_t slice_act_cr_qp_offset--><!--Device-int8_t slice_act_cr_qp_offset-End--> |
| int8_t slice_qp_delta | <!--Device-int8_t slice_qp_delta--><!--Device-int8_t slice_qp_delta-End--> |
| uint16_t reserved1 | <!--Device-uint16_t reserved1--><!--Device-uint16_t reserved1-End--> |
| [const StdVideoEncodeH265WeightTable*](capi--stdvideoencodeh265weighttable.md) pWeightTable | <!--Device-const StdVideoEncodeH265WeightTable* pWeightTable--><!--Device-const StdVideoEncodeH265WeightTable* pWeightTable-End--> |


