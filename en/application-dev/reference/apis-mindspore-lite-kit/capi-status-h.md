# status.h

<!--Kit: MindSpore Lite Kit-->
<!--Subsystem: AI-->
<!--Owner: @zhuguodong8-->
<!--Designer: @zhuguodong8; @jjfeing-->
<!--Tester: @principal87-->
<!--Adviser: @ge-yafang-->

## Overview

Provides the status codes of MindSpore Lite.

**File to include**: <mindspore/status.h>

**Library**: libmindspore_lite_ndk.so

**System capability**: SystemCapability.Ai.MindSpore

**Since**: 9

**Related module**: [MindSpore](capi-mindspore.md)

## Summary

### Enums

| Name                               | typedef Keyword| Description           |
|-----------------------------------|---|---------------|
| [OH_AI_CompCode](#oh_ai_compcode) | - | Defines MindSpore component codes.              |
| [OH_AI_Status](#oh_ai_status)     | OH_AI_Status  | Defines MindSpore status codes.|


## Enum Description

### OH_AI_CompCode

```c
enum OH_AI_CompCode
```

**Description**

Defines MindSpore component codes. 

**Since**: 9

| Enum Item                              | Description                   |
|-----------------------------------|-----------------------|
| OH_AI_COMPCODE_CORE = 0x00000000u | MindSpore Core code.|
| OH_AI_COMPCODE_MD = 0x10000000u   | MindSpore MindData code.|
| OH_AI_COMPCODE_ME = 0x20000000u   | MindSpore MindExpression code.|
| OH_AI_COMPCODE_MC = 0x30000000u   | MindSpore code.|
| OH_AI_COMPCODE_LITE = 0xF0000000u | MindSpore Lite code.   |


### OH_AI_Status

```c
enum OH_AI_Status
```

**Description**

Defines MindSpore status codes.

**Since**: 9

| Enum Item                                                                               | Description                          |
|------------------------------------------------------------------------------------|------------------------------|
| OH_AI_STATUS_SUCCESS = 0                                                           | The operation is successful.                   |
| OH_AI_STATUS_CORE_FAILED = OH_AI_COMPCODE_CORE \| 0x1                              | MindSpore Core execution failure.       |
| OH_AI_STATUS_LITE_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -1)                 | MindSpore Lite execution is abnormal.       |
| OH_AI_STATUS_LITE_NULLPTR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -2)               | The null pointer of MindSpore Lite is abnormal.      |
| OH_AI_STATUS_LITE_PARAM_INVALID = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -3)         | The parameter of MindSpore Lite is abnormal.     |
| OH_AI_STATUS_LITE_NO_CHANGE = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -4)             | MindSpore Lite is not changed.      |
| OH_AI_STATUS_LITE_SUCCESS_EXIT = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -5)          | MindSpore Lite is normal but exits.|
| OH_AI_STATUS_LITE_MEMORY_FAILED = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -6)         | MindSpore Lite fails to allocate memory.  |
| OH_AI_STATUS_LITE_NOT_SUPPORT = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -7)           | MindSpore Lite does not support the feature.   |
| OH_AI_STATUS_LITE_THREADPOOL_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -8)      | The thread pool of MindSpore Lite is abnormal.    |
| OH_AI_STATUS_LITE_UNINITIALIZED_OBJ = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -9)     | MindSpore Lite uninitialized.     |
| OH_AI_STATUS_LITE_OUT_OF_TENSOR_RANGE = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -100) | Executor-related error code. The value range is (-200, -100].<br>MindSpore Lite tensor overflow error.  |
| OH_AI_STATUS_LITE_INPUT_TENSOR_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -101)  | Executor-related error code. The value range is (-200, -100].<br>MindSpore Lite tensor input error. |
| OH_AI_STATUS_LITE_REENTRANT_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -102)     | Executor-related error code. The value range is (-200, -100].<br>MindSpore Lite function re-entry error.    |
| OH_AI_STATUS_LITE_GRAPH_FILE_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -200)    | Graph-related error code. The value range is (-300, -200].<br>MindSpore Lite graph file error.   |
| OH_AI_STATUS_LITE_NOT_FIND_OP = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -300)         | Operator-related error code. The value range is (-400, -300].<br>MindSpore Lite does not find the operator.  |
| OH_AI_STATUS_LITE_INVALID_OP_NAME = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -301)     | Operator-related error code. The value range is (-400, -300].<br>The operator of MindSpore Lite is invalid.      |
| OH_AI_STATUS_LITE_INVALID_OP_ATTR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -302)     | Operator-related error code. The value range is (-400, -300].<br>The operator of MindSpore Lite has an invalid hyperparameter.  |
| OH_AI_STATUS_LITE_OP_EXECUTE_FAILURE = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -303)  | Operator-related error code. The value range is (-400, -300].<br>The operator of MindSpore Lite fails to be executed.   |
| OH_AI_STATUS_LITE_FORMAT_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -400)        | Tensor-related error code. The value range is (-500, -400].<br>MindSpore Lite tensor format error.  |
| OH_AI_STATUS_LITE_INFER_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -500)         | Shape inference-related error code. The value range is (-600, -500].<br>MindSpore Lite shape inference error.   |
| OH_AI_STATUS_LITE_INFER_INVALID = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -501)       | Shape inference-related error code. The value range is (-600, -500].<br>Invalid shape inference of MindSpore Lite. |
| OH_AI_STATUS_LITE_INPUT_PARAM_INVALID = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -600) | User input-related error code. The value range is (-700, -600].<br>Invalid user input.|
| OH_AI_STATUS_LITE_AIPP_NOT_SUPPORTED = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -700) | Error code related to AI Pre-Process (AIPP). The value range is (-800, -700].<br>MindSpore Lite does not support AIPP.<br>**Since**: 23|
| OH_AI_STATUS_LITE_AIPP_INFER_ERROR = OH_AI_COMPCODE_LITE \| (0x0FFFFFFF & -701) | Error code related to AI Pre-Process (AIPP). The value range is (-800, -700].<br>MindSpore Lite fails to use AIPP for inference.<br>**Since**: 23|
