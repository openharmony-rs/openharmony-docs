# data_type.h

## Overview

Declares tensor data types.

**Library**: libmindspore_lite_ndk.so

**Since**: 9

**Related module**: [MindSpore](capi-mind-spore-lite-kit-mindspore.md)

## Summary

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AI_DataType](#oh_ai_datatype) | OH_AI_DataType | Declares tensor data types. |

### Macros

| Name | Description |
| -- | -- |
| MINDSPORE_INCLUDE_C_API_DATA_TYPE_C_H | Declares tensor data types.<br>**Since**: 9 |

## Enum type description

### OH_AI_DataType

```c
enum OH_AI_DataType
```

**Description**

Declares tensor data types.

<!--Device-OH_AI_DataType--><!--Device-OH_AI_DataType-End-->

**Since**: 9 /
#define MINDSPORE_INCLUDE_C_API_DATA_TYPE_C_H

#include <stdint.h>

extern "C" {

| Enum item | Description |
| -- | -- |
| OH_AI_DATATYPE_UNKNOWN = 0 |  |
| OH_AI_DATATYPE_OBJECTTYPE_STRING = 12 |  |
| OH_AI_DATATYPE_OBJECTTYPE_LIST = 13 |  |
| OH_AI_DATATYPE_OBJECTTYPE_TUPLE = 14 |  |
| OH_AI_DATATYPE_OBJECTTYPE_TENSOR = 17 |  |
| OH_AI_DATATYPE_NUMBERTYPE_BEGIN = 29 |  |
| OH_AI_DATATYPE_NUMBERTYPE_BOOL = 30 |  |
| OH_AI_DATATYPE_NUMBERTYPE_INT8 = 32 |  |
| OH_AI_DATATYPE_NUMBERTYPE_INT16 = 33 |  |
| OH_AI_DATATYPE_NUMBERTYPE_INT32 = 34 |  |
| OH_AI_DATATYPE_NUMBERTYPE_INT64 = 35 |  |
| OH_AI_DATATYPE_NUMBERTYPE_UINT8 = 37 |  |
| OH_AI_DATATYPE_NUMBERTYPE_UINT16 = 38 |  |
| OH_AI_DATATYPE_NUMBERTYPE_UINT32 = 39 |  |
| OH_AI_DATATYPE_NUMBERTYPE_UINT64 = 40 |  |
| OH_AI_DATATYPE_NUMBERTYPE_FLOAT16 = 42 |  |
| OH_AI_DATATYPE_NUMBERTYPE_FLOAT32 = 43 |  |
| OH_AI_DATATYPE_NUMBERTYPE_FLOAT64 = 44 |  |
| OH_AI_DATATYPE_NUMBERTYPE_END = 46 |  |
| OH_AI_DataTypeInvalid = INT32_MAX |  |


