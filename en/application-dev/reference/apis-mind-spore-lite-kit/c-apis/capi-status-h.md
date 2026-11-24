# status.h

## Overview

Provides the status codes of MindSpore Lite.

**Library**: libmindspore_lite_ndk.so

**Since**: 9

**Related module**: [MindSpore](capi-mind-spore-lite-kit-mindspore.md)

## Summary

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AI_CompCode](#oh_ai_compcode) | - | Defines the component code enumeration for MindSpore Lite.<br> Used to identify the component module to which a status code belongs. Each status code contains a component code part. Component codes are used to distinguish error codes from different modules. |
| [OH_AI_Status](#oh_ai_status) | OH_AI_Status | Defines the status code enumeration for MindSpore Lite.<br> Used to indicate the return status of MindSpore Lite API calls, including success and various error conditions. Status codes are divided into different ranges, each corresponding to a specific type of error or status. Common error code ranges: (-100,-1] for general errors, (-200,-100] for executor errors, (-300,-200] for graph errors, (-400,-300] for operator errors, (-500,-400] for tensor errors, (-600,-500] for shape inference errors, (-700,-600] for user input parameter errors, (-800,-700] for AIPP module errors. |

### Macros

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

<!--Device-enum OH_AI_CompCode--><!--Device-enum OH_AI_CompCode-End-->

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_AI_COMPCODE_CORE = 0x00000000u | Core component code.<br><!--Device-OH_AI_COMPCODE_CORE = 0x00000000u--><!--Device-OH_AI_COMPCODE_CORE = 0x00000000u-End--> |
| OH_AI_COMPCODE_MD = 0x10000000u | MD component code.<br><!--Device-OH_AI_COMPCODE_MD = 0x10000000u--><!--Device-OH_AI_COMPCODE_MD = 0x10000000u-End--> |
| OH_AI_COMPCODE_ME = 0x20000000u | ME component code.<br><!--Device-OH_AI_COMPCODE_ME = 0x20000000u--><!--Device-OH_AI_COMPCODE_ME = 0x20000000u-End--> |
| OH_AI_COMPCODE_MC = 0x30000000u | MC component code.<br><!--Device-OH_AI_COMPCODE_MC = 0x30000000u--><!--Device-OH_AI_COMPCODE_MC = 0x30000000u-End--> |
| OH_AI_COMPCODE_LITE = 0xF0000000u | Lite component code.<br><!--Device-OH_AI_COMPCODE_LITE = 0xF0000000u--><!--Device-OH_AI_COMPCODE_LITE = 0xF0000000u-End--> |

### OH_AI_Status

```c
enum OH_AI_Status
```

**Description**

Defines the status code enumeration for MindSpore Lite.<br> Used to indicate the return status of MindSpore Lite API calls, including success and various error conditions. Status codes are divided into different ranges, each corresponding to a specific type of error or status. Common error code ranges: (-100,-1] for general errors, (-200,-100] for executor errors, (-300,-200] for graph errors, (-400,-300] for operator errors, (-500,-400] for tensor errors, (-600,-500] for shape inference errors, (-700,-600] for user input parameter errors, (-800,-700] for AIPP module errors.

<!--Device-enum OH_AI_Status--><!--Device-enum OH_AI_Status-End-->

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_AI_STATUS_SUCCESS = 0 | Success.<br><!--Device-OH_AI_STATUS_SUCCESS = 0--><!--Device-OH_AI_STATUS_SUCCESS = 0-End--> |
| OH_AI_STATUS_CORE_FAILED = OH_AI_COMPCODE_CORE \| 0x1 | Core failure.<br><!--Device-OH_AI_STATUS_CORE_FAILED = OH_AI_COMPCODE_CORE \| 0x1--><!--Device-OH_AI_STATUS_CORE_FAILED = OH_AI_COMPCODE_CORE \| 0x1-End--> |
| OH_AI_STATUS_LITE_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -1) | Common error.<br><!--Device-OH_AI_STATUS_LITE_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -1)--><!--Device-OH_AI_STATUS_LITE_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -1)-End--> |
| OH_AI_STATUS_LITE_NULLPTR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -2) | Null pointer returned.<br><!--Device-OH_AI_STATUS_LITE_NULLPTR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -2)--><!--Device-OH_AI_STATUS_LITE_NULLPTR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -2)-End--> |
| OH_AI_STATUS_LITE_PARAM_INVALID = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -3) | Invalid parameter.<br><!--Device-OH_AI_STATUS_LITE_PARAM_INVALID = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -3)--><!--Device-OH_AI_STATUS_LITE_PARAM_INVALID = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -3)-End--> |
| OH_AI_STATUS_LITE_NO_CHANGE = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -4) | No change.<br><!--Device-OH_AI_STATUS_LITE_NO_CHANGE = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -4)--><!--Device-OH_AI_STATUS_LITE_NO_CHANGE = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -4)-End--> |
| OH_AI_STATUS_LITE_SUCCESS_EXIT = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -5) | No error but exit.<br><!--Device-OH_AI_STATUS_LITE_SUCCESS_EXIT = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -5)--><!--Device-OH_AI_STATUS_LITE_SUCCESS_EXIT = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -5)-End--> |
| OH_AI_STATUS_LITE_MEMORY_FAILED = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -6) | Failed to create memory.<br><!--Device-OH_AI_STATUS_LITE_MEMORY_FAILED = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -6)--><!--Device-OH_AI_STATUS_LITE_MEMORY_FAILED = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -6)-End--> |
| OH_AI_STATUS_LITE_NOT_SUPPORT = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -7) | Not support.<br><!--Device-OH_AI_STATUS_LITE_NOT_SUPPORT = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -7)--><!--Device-OH_AI_STATUS_LITE_NOT_SUPPORT = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -7)-End--> |
| OH_AI_STATUS_LITE_THREADPOOL_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -8) | Error occurred in thread pool.<br><!--Device-OH_AI_STATUS_LITE_THREADPOOL_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -8)--><!--Device-OH_AI_STATUS_LITE_THREADPOOL_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -8)-End--> |
| OH_AI_STATUS_LITE_UNINITIALIZED_OBJ = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -9) | Object is not initialized.<br><!--Device-OH_AI_STATUS_LITE_UNINITIALIZED_OBJ = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -9)--><!--Device-OH_AI_STATUS_LITE_UNINITIALIZED_OBJ = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -9)-End--> |
| OH_AI_STATUS_LITE_OUT_OF_TENSOR_RANGE = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -100) | Failed to check tensor range.<br><!--Device-OH_AI_STATUS_LITE_OUT_OF_TENSOR_RANGE = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -100)--><!--Device-OH_AI_STATUS_LITE_OUT_OF_TENSOR_RANGE = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -100)-End--> |
| OH_AI_STATUS_LITE_INPUT_TENSOR_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -101) | Failed to check input tensor.<br><!--Device-OH_AI_STATUS_LITE_INPUT_TENSOR_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -101)--><!--Device-OH_AI_STATUS_LITE_INPUT_TENSOR_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -101)-End--> |
| OH_AI_STATUS_LITE_REENTRANT_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -102) | Executor is already running.<br><!--Device-OH_AI_STATUS_LITE_REENTRANT_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -102)--><!--Device-OH_AI_STATUS_LITE_REENTRANT_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -102)-End--> |
| OH_AI_STATUS_LITE_GRAPH_FILE_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -200) | Failed to verify graph file.<br><!--Device-OH_AI_STATUS_LITE_GRAPH_FILE_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -200)--><!--Device-OH_AI_STATUS_LITE_GRAPH_FILE_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -200)-End--> |
| OH_AI_STATUS_LITE_NOT_FIND_OP = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -300) | Failed to find operator.<br><!--Device-OH_AI_STATUS_LITE_NOT_FIND_OP = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -300)--><!--Device-OH_AI_STATUS_LITE_NOT_FIND_OP = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -300)-End--> |
| OH_AI_STATUS_LITE_INVALID_OP_NAME = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -301) | Invalid operator name.<br><!--Device-OH_AI_STATUS_LITE_INVALID_OP_NAME = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -301)--><!--Device-OH_AI_STATUS_LITE_INVALID_OP_NAME = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -301)-End--> |
| OH_AI_STATUS_LITE_INVALID_OP_ATTR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -302) | Invalid operator attribute.<br><!--Device-OH_AI_STATUS_LITE_INVALID_OP_ATTR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -302)--><!--Device-OH_AI_STATUS_LITE_INVALID_OP_ATTR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -302)-End--> |
| OH_AI_STATUS_LITE_OP_EXECUTE_FAILURE = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -303) | Failed to execute operator.<br><!--Device-OH_AI_STATUS_LITE_OP_EXECUTE_FAILURE = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -303)--><!--Device-OH_AI_STATUS_LITE_OP_EXECUTE_FAILURE = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -303)-End--> |
| OH_AI_STATUS_LITE_FORMAT_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -400) | Failed to check tensor format.<br><!--Device-OH_AI_STATUS_LITE_FORMAT_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -400)--><!--Device-OH_AI_STATUS_LITE_FORMAT_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -400)-End--> |
| OH_AI_STATUS_LITE_INFER_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -500) | Failed to infer shape.<br><!--Device-OH_AI_STATUS_LITE_INFER_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -500)--><!--Device-OH_AI_STATUS_LITE_INFER_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -500)-End--> |
| OH_AI_STATUS_LITE_INFER_INVALID = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -501) | Invalid shape inference before runtime.<br><!--Device-OH_AI_STATUS_LITE_INFER_INVALID = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -501)--><!--Device-OH_AI_STATUS_LITE_INFER_INVALID = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -501)-End--> |
| OH_AI_STATUS_LITE_INPUT_PARAM_INVALID = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -600) | Invalid input parameter from user.<br><!--Device-OH_AI_STATUS_LITE_INPUT_PARAM_INVALID = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -600)--><!--Device-OH_AI_STATUS_LITE_INPUT_PARAM_INVALID = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -600)-End--> |
| OH_AI_STATUS_LITE_AIPP_NOT_SUPPORTED = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -700) | AIPP is not supported.<br>**Since**: 23<br><!--Device-OH_AI_STATUS_LITE_AIPP_NOT_SUPPORTED = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -700)--><!--Device-OH_AI_STATUS_LITE_AIPP_NOT_SUPPORTED = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -700)-End--> |
| OH_AI_STATUS_LITE_AIPP_INFER_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -701) | Failed to infer with AIPP.<br>**Since**: 23<br><!--Device-OH_AI_STATUS_LITE_AIPP_INFER_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -701)--><!--Device-OH_AI_STATUS_LITE_AIPP_INFER_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -701)-End--> |


