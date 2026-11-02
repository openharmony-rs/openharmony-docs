# StdVideoEncodeH264ReferenceListsInfo

## Overview

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [StdVideoEncodeH264ReferenceListsInfoFlags](capi--stdvideoencodeh264referencelistsinfoflags.md) flags |  |
| uint8_t num_ref_idx_l0_active_minus1 |  |
| uint8_t num_ref_idx_l1_active_minus1 |  |
| uint8_t RefPicList0[STD_VIDEO_H264_MAX_NUM_LIST_REF] |  |
| uint8_t RefPicList1[STD_VIDEO_H264_MAX_NUM_LIST_REF] |  |
| uint8_t refList0ModOpCount |  |
| uint8_t refList1ModOpCount |  |
| uint8_t refPicMarkingOpCount |  |
| uint8_t reserved1[7] |  |
| [const StdVideoEncodeH264RefListModEntry*](capi--stdvideoencodeh264reflistmodentry.md) pRefList0ModOperations |  |
| [const StdVideoEncodeH264RefListModEntry*](capi--stdvideoencodeh264reflistmodentry.md) pRefList1ModOperations |  |
| [const StdVideoEncodeH264RefPicMarkingEntry*](capi--stdvideoencodeh264refpicmarkingentry.md) pRefPicMarkingOperations |  |


