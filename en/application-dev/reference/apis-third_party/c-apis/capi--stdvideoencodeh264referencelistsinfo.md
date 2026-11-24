# StdVideoEncodeH264ReferenceListsInfo

## Overview

<!--Device-struct StdVideoEncodeH264ReferenceListsInfo {...}--><!--Device-struct StdVideoEncodeH264ReferenceListsInfo {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [StdVideoEncodeH264ReferenceListsInfoFlags](capi--stdvideoencodeh264referencelistsinfoflags.md) flags | <!--Device-StdVideoEncodeH264ReferenceListsInfoFlags flags--><!--Device-StdVideoEncodeH264ReferenceListsInfoFlags flags-End--> |
| uint8_t num_ref_idx_l0_active_minus1 | <!--Device-uint8_t num_ref_idx_l0_active_minus1--><!--Device-uint8_t num_ref_idx_l0_active_minus1-End--> |
| uint8_t num_ref_idx_l1_active_minus1 | <!--Device-uint8_t num_ref_idx_l1_active_minus1--><!--Device-uint8_t num_ref_idx_l1_active_minus1-End--> |
| uint8_t RefPicList0[STD_VIDEO_H264_MAX_NUM_LIST_REF] | <!--Device-uint8_t RefPicList0[STD_VIDEO_H264_MAX_NUM_LIST_REF]--><!--Device-uint8_t RefPicList0[STD_VIDEO_H264_MAX_NUM_LIST_REF]-End--> |
| uint8_t RefPicList1[STD_VIDEO_H264_MAX_NUM_LIST_REF] | <!--Device-uint8_t RefPicList1[STD_VIDEO_H264_MAX_NUM_LIST_REF]--><!--Device-uint8_t RefPicList1[STD_VIDEO_H264_MAX_NUM_LIST_REF]-End--> |
| uint8_t refList0ModOpCount | <!--Device-uint8_t refList0ModOpCount--><!--Device-uint8_t refList0ModOpCount-End--> |
| uint8_t refList1ModOpCount | <!--Device-uint8_t refList1ModOpCount--><!--Device-uint8_t refList1ModOpCount-End--> |
| uint8_t refPicMarkingOpCount | <!--Device-uint8_t refPicMarkingOpCount--><!--Device-uint8_t refPicMarkingOpCount-End--> |
| uint8_t reserved1[7] | <!--Device-uint8_t reserved1[7]--><!--Device-uint8_t reserved1[7]-End--> |
| [const StdVideoEncodeH264RefListModEntry*](capi--stdvideoencodeh264reflistmodentry.md) pRefList0ModOperations | <!--Device-const StdVideoEncodeH264RefListModEntry* pRefList0ModOperations--><!--Device-const StdVideoEncodeH264RefListModEntry* pRefList0ModOperations-End--> |
| [const StdVideoEncodeH264RefListModEntry*](capi--stdvideoencodeh264reflistmodentry.md) pRefList1ModOperations | <!--Device-const StdVideoEncodeH264RefListModEntry* pRefList1ModOperations--><!--Device-const StdVideoEncodeH264RefListModEntry* pRefList1ModOperations-End--> |
| [const StdVideoEncodeH264RefPicMarkingEntry*](capi--stdvideoencodeh264refpicmarkingentry.md) pRefPicMarkingOperations | <!--Device-const StdVideoEncodeH264RefPicMarkingEntry* pRefPicMarkingOperations--><!--Device-const StdVideoEncodeH264RefPicMarkingEntry* pRefPicMarkingOperations-End--> |


