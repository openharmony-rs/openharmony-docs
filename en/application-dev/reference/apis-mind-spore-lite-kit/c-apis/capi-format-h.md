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

<!--Device-OH_AI_Format--><!--Device-OH_AI_Format-End-->

**Since**: 9 /
#define MINDSPORE_INCLUDE_C_API_FORMAT_C_H

extern "C" {

| Enum item | Description |
| -- | -- |
| OH_AI_FORMAT_NCHW = 0 |  |
| OH_AI_FORMAT_NHWC = 1 |  |
| OH_AI_FORMAT_NHWC4 = 2 |  |
| OH_AI_FORMAT_HWKC = 3 |  |
| OH_AI_FORMAT_HWCK = 4 |  |
| OH_AI_FORMAT_KCHW = 5 |  |
| OH_AI_FORMAT_CKHW = 6 |  |
| OH_AI_FORMAT_KHWC = 7 |  |
| OH_AI_FORMAT_CHWK = 8 |  |
| OH_AI_FORMAT_HW = 9 |  |
| OH_AI_FORMAT_HW4 = 10 |  |
| OH_AI_FORMAT_NC = 11 |  |
| OH_AI_FORMAT_NC4 = 12 |  |
| OH_AI_FORMAT_NC4HW4 = 13 |  |
| OH_AI_FORMAT_NCDHW = 15 |  |
| OH_AI_FORMAT_NWC = 16 |  |
| OH_AI_FORMAT_NCW = 17 |  |


