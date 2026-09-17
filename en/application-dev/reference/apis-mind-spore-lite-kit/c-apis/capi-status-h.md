# status.h

## Overview

Provides the status codes of MindSpore Lite.

**Library**: libmindspore_lite_ndk.so

**Since**: 9

**Related module**: [MindSpore](capi-mindspore.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AI_CompCode](#oh_ai_compcode) | - | Defines the component code enumeration for MindSpore Lite.<br> Used to identify the component module to which a status code belongs. Each status code contains a component code part. Component codes are used to distinguish error codes from different modules. |
| [OH_AI_Status](#oh_ai_status) | OH_AI_Status | Defines the status code enumeration for MindSpore Lite.<br> Used to indicate the return status of MindSpore Lite API calls, including success and various error conditions. Status codes are divided into different ranges, each corresponding to a specific type of error or status. Common error code ranges: (-100,-1] for general errors, (-200,-100] for executor errors, (-300,-200] for graph errors, (-400,-300] for operator errors, (-500,-400] for tensor errors, (-600,-500] for shape inference errors, (-700,-600] for user input parameter errors, (-800,-700] for AIPP module errors. |

### Macro

| Name | Description |
| -- | -- |
| MINDSPORE_INCLUDE_C_API_STATUS_C_H | Provides the status codes of MindSpore Lite.<br>**Since**: 9 |

## Enum type description

### OH_AI_CompCode

```c
enum OH_AI_CompCode
```

**Description**

Defines the component code enumeration for MindSpore Lite.<br> Used to identify the component module to which a status code belongs. Each status code contains a component code part. Component codes are used to distinguish error codes from different modules.

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_AI_COMPCODE_CORE = 0x00000000u | Core component code. |
| OH_AI_COMPCODE_MD = 0x10000000u | MD component code. |
| OH_AI_COMPCODE_ME = 0x20000000u | ME component code. |
| OH_AI_COMPCODE_MC = 0x30000000u | MC component code. |
| OH_AI_COMPCODE_LITE = 0xF0000000u | Lite component code. |

### OH_AI_Status

```c
enum OH_AI_Status
```

**Description**

Defines the status code enumeration for MindSpore Lite.<br> Used to indicate the return status of MindSpore Lite API calls, including success and various error conditions. Status codes are divided into different ranges, each corresponding to a specific type of error or status. Common error code ranges: (-100,-1] for general errors, (-200,-100] for executor errors, (-300,-200] for graph errors, (-400,-300] for operator errors, (-500,-400] for tensor errors, (-600,-500] for shape inference errors, (-700,-600] for user input parameter errors, (-800,-700] for AIPP module errors.

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_AI_STATUS_SUCCESS = 0 | Success. |
| OH_AI_STATUS_CORE_FAILED = OH_AI_COMPCODE_CORE \| 0x1 | Core failure. |
| OH_AI_STATUS_LITE_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -1) | Common error. |
| OH_AI_STATUS_LITE_NULLPTR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -2) | Null pointer returned. |
| OH_AI_STATUS_LITE_PARAM_INVALID = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -3) | Invalid parameter. |
| OH_AI_STATUS_LITE_NO_CHANGE = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -4) | No change. |
| OH_AI_STATUS_LITE_SUCCESS_EXIT = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -5) | No error but exit. |
| OH_AI_STATUS_LITE_MEMORY_FAILED = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -6) | Failed to create memory. |
| OH_AI_STATUS_LITE_NOT_SUPPORT = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -7) | Not support. |
| OH_AI_STATUS_LITE_THREADPOOL_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -8) | Error occurred in thread pool. |
| OH_AI_STATUS_LITE_UNINITIALIZED_OBJ = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -9) | Object is not initialized. |
| OH_AI_STATUS_LITE_OUT_OF_TENSOR_RANGE = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -100) | Failed to check tensor range. |
| OH_AI_STATUS_LITE_INPUT_TENSOR_ERROR = | Failed to check input tensor. |
| OH_AI_STATUS_LITE_REENTRANT_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -102) | Executor is already running. |
| OH_AI_STATUS_LITE_GRAPH_FILE_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -200) | Failed to verify graph file. |
| OH_AI_STATUS_LITE_NOT_FIND_OP = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -300) | Failed to find operator. |
| OH_AI_STATUS_LITE_INVALID_OP_NAME = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -301) | Invalid operator name. |
| OH_AI_STATUS_LITE_INVALID_OP_ATTR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -302) | Invalid operator attribute. |
| OH_AI_STATUS_LITE_OP_EXECUTE_FAILURE = | Failed to execute operator. |
| OH_AI_STATUS_LITE_FORMAT_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -400) | Failed to check tensor format. |
| OH_AI_STATUS_LITE_INFER_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -500) | Failed to infer shape. |
| OH_AI_STATUS_LITE_INFER_INVALID = | Invalid shape inference before runtime. |
| OH_AI_STATUS_LITE_INPUT_PARAM_INVALID = | Invalid input parameter from user. |
| OH_AI_STATUS_LITE_AIPP_NOT_SUPPORTED = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -700) | AIPP is not supported.<br>**Since**: 23 |
| OH_AI_STATUS_LITE_AIPP_INFER_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -701) | Failed to infer with AIPP.<br>**Since**: 23 |


