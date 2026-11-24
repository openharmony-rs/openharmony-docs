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

<!--Device-enum OH_AI_DataType--><!--Device-enum OH_AI_DataType-End-->

**Since**: 9 /
#define MINDSPORE_INCLUDE_C_API_DATA_TYPE_C_H

#include <stdint.h>

extern "C" {

| Enum item | Description |
| -- | -- |
| OH_AI_DATATYPE_UNKNOWN = 0 | <!--Device-OH_AI_DATATYPE_UNKNOWN = 0--><!--Device-OH_AI_DATATYPE_UNKNOWN = 0-End--> |
| OH_AI_DATATYPE_OBJECTTYPE_STRING = 12 | <!--Device-OH_AI_DATATYPE_OBJECTTYPE_STRING = 12--><!--Device-OH_AI_DATATYPE_OBJECTTYPE_STRING = 12-End--> |
| OH_AI_DATATYPE_OBJECTTYPE_LIST = 13 | <!--Device-OH_AI_DATATYPE_OBJECTTYPE_LIST = 13--><!--Device-OH_AI_DATATYPE_OBJECTTYPE_LIST = 13-End--> |
| OH_AI_DATATYPE_OBJECTTYPE_TUPLE = 14 | <!--Device-OH_AI_DATATYPE_OBJECTTYPE_TUPLE = 14--><!--Device-OH_AI_DATATYPE_OBJECTTYPE_TUPLE = 14-End--> |
| OH_AI_DATATYPE_OBJECTTYPE_TENSOR = 17 | <!--Device-OH_AI_DATATYPE_OBJECTTYPE_TENSOR = 17--><!--Device-OH_AI_DATATYPE_OBJECTTYPE_TENSOR = 17-End--> |
| OH_AI_DATATYPE_NUMBERTYPE_BEGIN = 29 | <!--Device-OH_AI_DATATYPE_NUMBERTYPE_BEGIN = 29--><!--Device-OH_AI_DATATYPE_NUMBERTYPE_BEGIN = 29-End--> |
| OH_AI_DATATYPE_NUMBERTYPE_BOOL = 30 | <!--Device-OH_AI_DATATYPE_NUMBERTYPE_BOOL = 30--><!--Device-OH_AI_DATATYPE_NUMBERTYPE_BOOL = 30-End--> |
| OH_AI_DATATYPE_NUMBERTYPE_INT8 = 32 | <!--Device-OH_AI_DATATYPE_NUMBERTYPE_INT8 = 32--><!--Device-OH_AI_DATATYPE_NUMBERTYPE_INT8 = 32-End--> |
| OH_AI_DATATYPE_NUMBERTYPE_INT16 = 33 | <!--Device-OH_AI_DATATYPE_NUMBERTYPE_INT16 = 33--><!--Device-OH_AI_DATATYPE_NUMBERTYPE_INT16 = 33-End--> |
| OH_AI_DATATYPE_NUMBERTYPE_INT32 = 34 | <!--Device-OH_AI_DATATYPE_NUMBERTYPE_INT32 = 34--><!--Device-OH_AI_DATATYPE_NUMBERTYPE_INT32 = 34-End--> |
| OH_AI_DATATYPE_NUMBERTYPE_INT64 = 35 | <!--Device-OH_AI_DATATYPE_NUMBERTYPE_INT64 = 35--><!--Device-OH_AI_DATATYPE_NUMBERTYPE_INT64 = 35-End--> |
| OH_AI_DATATYPE_NUMBERTYPE_UINT8 = 37 | <!--Device-OH_AI_DATATYPE_NUMBERTYPE_UINT8 = 37--><!--Device-OH_AI_DATATYPE_NUMBERTYPE_UINT8 = 37-End--> |
| OH_AI_DATATYPE_NUMBERTYPE_UINT16 = 38 | <!--Device-OH_AI_DATATYPE_NUMBERTYPE_UINT16 = 38--><!--Device-OH_AI_DATATYPE_NUMBERTYPE_UINT16 = 38-End--> |
| OH_AI_DATATYPE_NUMBERTYPE_UINT32 = 39 | <!--Device-OH_AI_DATATYPE_NUMBERTYPE_UINT32 = 39--><!--Device-OH_AI_DATATYPE_NUMBERTYPE_UINT32 = 39-End--> |
| OH_AI_DATATYPE_NUMBERTYPE_UINT64 = 40 | <!--Device-OH_AI_DATATYPE_NUMBERTYPE_UINT64 = 40--><!--Device-OH_AI_DATATYPE_NUMBERTYPE_UINT64 = 40-End--> |
| OH_AI_DATATYPE_NUMBERTYPE_FLOAT16 = 42 | <!--Device-OH_AI_DATATYPE_NUMBERTYPE_FLOAT16 = 42--><!--Device-OH_AI_DATATYPE_NUMBERTYPE_FLOAT16 = 42-End--> |
| OH_AI_DATATYPE_NUMBERTYPE_FLOAT32 = 43 | <!--Device-OH_AI_DATATYPE_NUMBERTYPE_FLOAT32 = 43--><!--Device-OH_AI_DATATYPE_NUMBERTYPE_FLOAT32 = 43-End--> |
| OH_AI_DATATYPE_NUMBERTYPE_FLOAT64 = 44 | <!--Device-OH_AI_DATATYPE_NUMBERTYPE_FLOAT64 = 44--><!--Device-OH_AI_DATATYPE_NUMBERTYPE_FLOAT64 = 44-End--> |
| OH_AI_DATATYPE_NUMBERTYPE_END = 46 | <!--Device-OH_AI_DATATYPE_NUMBERTYPE_END = 46--><!--Device-OH_AI_DATATYPE_NUMBERTYPE_END = 46-End--> |
| OH_AI_DataTypeInvalid = INT32_MAX | <!--Device-OH_AI_DataTypeInvalid = INT32_MAX--><!--Device-OH_AI_DataTypeInvalid = INT32_MAX-End--> |


