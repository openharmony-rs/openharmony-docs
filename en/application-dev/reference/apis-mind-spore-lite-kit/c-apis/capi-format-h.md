# format.h

## Overview

Declares tensor data formats.

**Library**: libmindspore_lite_ndk.so

**Since**: 9

**Related module**: [MindSpore](capi-mind-spore-lite-kit-mindspore.md)

## Summary

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AI_Format](#oh_ai_format) | OH_AI_Format | Declares tensor data formats. |

### Macros

| Name | Description |
| -- | -- |
| MINDSPORE_INCLUDE_C_API_FORMAT_C_H | Declares tensor data formats.<br>**Since**: 9 |

## Enum type description

### OH_AI_Format

```c
enum OH_AI_Format
```

**Description**

Declares tensor data formats.

<!--Device-enum OH_AI_Format--><!--Device-enum OH_AI_Format-End-->

**Since**: 9 /
#define MINDSPORE_INCLUDE_C_API_FORMAT_C_H

extern "C" {

| Enum item | Description |
| -- | -- |
| OH_AI_FORMAT_NCHW = 0 | <!--Device-OH_AI_FORMAT_NCHW = 0--><!--Device-OH_AI_FORMAT_NCHW = 0-End--> |
| OH_AI_FORMAT_NHWC = 1 | <!--Device-OH_AI_FORMAT_NHWC = 1--><!--Device-OH_AI_FORMAT_NHWC = 1-End--> |
| OH_AI_FORMAT_NHWC4 = 2 | <!--Device-OH_AI_FORMAT_NHWC4 = 2--><!--Device-OH_AI_FORMAT_NHWC4 = 2-End--> |
| OH_AI_FORMAT_HWKC = 3 | <!--Device-OH_AI_FORMAT_HWKC = 3--><!--Device-OH_AI_FORMAT_HWKC = 3-End--> |
| OH_AI_FORMAT_HWCK = 4 | <!--Device-OH_AI_FORMAT_HWCK = 4--><!--Device-OH_AI_FORMAT_HWCK = 4-End--> |
| OH_AI_FORMAT_KCHW = 5 | <!--Device-OH_AI_FORMAT_KCHW = 5--><!--Device-OH_AI_FORMAT_KCHW = 5-End--> |
| OH_AI_FORMAT_CKHW = 6 | <!--Device-OH_AI_FORMAT_CKHW = 6--><!--Device-OH_AI_FORMAT_CKHW = 6-End--> |
| OH_AI_FORMAT_KHWC = 7 | <!--Device-OH_AI_FORMAT_KHWC = 7--><!--Device-OH_AI_FORMAT_KHWC = 7-End--> |
| OH_AI_FORMAT_CHWK = 8 | <!--Device-OH_AI_FORMAT_CHWK = 8--><!--Device-OH_AI_FORMAT_CHWK = 8-End--> |
| OH_AI_FORMAT_HW = 9 | <!--Device-OH_AI_FORMAT_HW = 9--><!--Device-OH_AI_FORMAT_HW = 9-End--> |
| OH_AI_FORMAT_HW4 = 10 | <!--Device-OH_AI_FORMAT_HW4 = 10--><!--Device-OH_AI_FORMAT_HW4 = 10-End--> |
| OH_AI_FORMAT_NC = 11 | <!--Device-OH_AI_FORMAT_NC = 11--><!--Device-OH_AI_FORMAT_NC = 11-End--> |
| OH_AI_FORMAT_NC4 = 12 | <!--Device-OH_AI_FORMAT_NC4 = 12--><!--Device-OH_AI_FORMAT_NC4 = 12-End--> |
| OH_AI_FORMAT_NC4HW4 = 13 | <!--Device-OH_AI_FORMAT_NC4HW4 = 13--><!--Device-OH_AI_FORMAT_NC4HW4 = 13-End--> |
| OH_AI_FORMAT_NCDHW = 15 | <!--Device-OH_AI_FORMAT_NCDHW = 15--><!--Device-OH_AI_FORMAT_NCDHW = 15-End--> |
| OH_AI_FORMAT_NWC = 16 | <!--Device-OH_AI_FORMAT_NWC = 16--><!--Device-OH_AI_FORMAT_NWC = 16-End--> |
| OH_AI_FORMAT_NCW = 17 | <!--Device-OH_AI_FORMAT_NCW = 17--><!--Device-OH_AI_FORMAT_NCW = 17-End--> |


