# StdVideoEncodeH264SliceHeader

## Overview

<!--Device-struct StdVideoEncodeH264SliceHeader {...}--><!--Device-struct StdVideoEncodeH264SliceHeader {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [StdVideoEncodeH264SliceHeaderFlags](capi--stdvideoencodeh264sliceheaderflags.md) flags | <!--Device-StdVideoEncodeH264SliceHeaderFlags flags--><!--Device-StdVideoEncodeH264SliceHeaderFlags flags-End--> |
| uint32_t first_mb_in_slice | <!--Device-uint32_t first_mb_in_slice--><!--Device-uint32_t first_mb_in_slice-End--> |
| StdVideoH264SliceType slice_type | <!--Device-StdVideoH264SliceType slice_type--><!--Device-StdVideoH264SliceType slice_type-End--> |
| int8_t slice_alpha_c0_offset_div2 | <!--Device-int8_t slice_alpha_c0_offset_div2--><!--Device-int8_t slice_alpha_c0_offset_div2-End--> |
| int8_t slice_beta_offset_div2 | <!--Device-int8_t slice_beta_offset_div2--><!--Device-int8_t slice_beta_offset_div2-End--> |
| int8_t slice_qp_delta | <!--Device-int8_t slice_qp_delta--><!--Device-int8_t slice_qp_delta-End--> |
| uint8_t reserved1 | <!--Device-uint8_t reserved1--><!--Device-uint8_t reserved1-End--> |
| StdVideoH264CabacInitIdc cabac_init_idc | <!--Device-StdVideoH264CabacInitIdc cabac_init_idc--><!--Device-StdVideoH264CabacInitIdc cabac_init_idc-End--> |
| StdVideoH264DisableDeblockingFilterIdc disable_deblocking_filter_idc | <!--Device-StdVideoH264DisableDeblockingFilterIdc disable_deblocking_filter_idc--><!--Device-StdVideoH264DisableDeblockingFilterIdc disable_deblocking_filter_idc-End--> |
| [const StdVideoEncodeH264WeightTable*](capi--stdvideoencodeh264weighttable.md) pWeightTable | <!--Device-const StdVideoEncodeH264WeightTable* pWeightTable--><!--Device-const StdVideoEncodeH264WeightTable* pWeightTable-End--> |


