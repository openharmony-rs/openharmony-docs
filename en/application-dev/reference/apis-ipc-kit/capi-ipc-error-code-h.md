# ipc_error_code.h
<!--Kit: IPC Kit-->
<!--Subsystem: Communication-->
<!--Owner: @xdx19211@luodonghui0157-->
<!--Designer: @zhaopeng_gitee-->
<!--Tester: @maxiaorong-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=98355c316452dae3a7c90b55e4a4861818921408 translatedAt=2026-11-04T03:40:15.610Z pushedAt=2026-11-04T10:13:14.841Z nl=1 -->

## Overview

Provides IPC error code definitions for identifying and handling various errors that may occur during IPC communication. Based on the returned error codes, you can quickly locate the cause of issues, such as parameter errors, serialization failures, memory allocation failures, and remote object death, and take appropriate error handling measures.

**File to include**: <IPCKit/ipc_error_code.h>

**Library**: libipc_capi.so

**System capability**: SystemCapability.Communication.IPC.Core

**Supported device types** This API is available for all device types. You can determine whether the function is available by checking the system capability SystemCapability.Communication.IPC.Core.

**Since**: 12

**Related module**: [OHIPCErrorCode](capi-ohipcerrorcode.md)

## Summary

### Enums

| Name| typedef Keyword| Description|
| ---- | ------------- | ---- |
| [OH_IPC_ErrorCode](#oh_ipc_errorcode) | OH_IPC_ErrorCode | Enumerates the IPC error codes. |

## Enum Description

### OH_IPC_ErrorCode

```C
enum OH_IPC_ErrorCode
```

**Description**

Enumerates the IPC error codes.

**Since**: 12

| Enum Item | Description |
| ------ | ---- |
| OH_IPC_SUCCESS = 0 | Operation success. |
| OH_IPC_ERROR_CODE_BASE = 1901000 | Start value of the error code range. |
| OH_IPC_CHECK_PARAM_ERROR = OH_IPC_ERROR_CODE_BASE | Invalid parameter. This error code is returned when an input parameter is a null pointer, a parameter value is out of the valid range, or a parameter type does not match. Developers should check the validity and legality of the parameters. |
| OH_IPC_PARCEL_WRITE_ERROR = OH_IPC_ERROR_CODE_BASE + 1 | Failed to write data to the serialized object. This error may occur when memory is insufficient during data serialization or the data format is not supported. Developers should check whether the data size and format meet the requirements. |
| OH_IPC_PARCEL_READ_ERROR = OH_IPC_ERROR_CODE_BASE + 2 | Failed to read data from the serialized object. This error may occur when the length of the data to be read exceeds the actual data length or the data format does not match. Developers should check whether the data reading order and data format are correct. |
| OH_IPC_MEM_ALLOCATOR_ERROR = OH_IPC_ERROR_CODE_BASE + 3 | Memory allocation failed. This error code is returned when the system memory is insufficient or the memory allocator is abnormal. Developers should check the memory usage, release unnecessary resources, and retry. |
| OH_IPC_CODE_OUT_OF_RANGE = OH_IPC_ERROR_CODE_BASE + 4 | The command word is out of the defined range [0x01, 0x00FFFFFF]. This error code is returned when the command word used for IPC communication is not within the valid range. Developers should check whether the command word definition complies with the specification. |
| OH_IPC_DEAD_REMOTE_OBJECT = OH_IPC_ERROR_CODE_BASE + 5 | The remote object is dead. This error code is returned when the peer process of the IPC communication has exited or the remote object has been destroyed. Developers should re-establish the connection or use an alternative service. |
| OH_IPC_INVALID_USER_ERROR_CODE = OH_IPC_ERROR_CODE_BASE + 6 | The user-defined error code is out of the range [1909000, 1909999]. This error code is returned when the custom error code set by the developer is not within the allowed range. Developers should ensure that the custom error code is within the valid range. |
| OH_IPC_INNER_ERROR = OH_IPC_ERROR_CODE_BASE + 7 | Internal IPC error. This error code is returned when an unknown error occurs inside the IPC system. Developers can record logs and contact technical support or retry later. |
| OH_IPC_ERROR_CODE_MAX = OH_IPC_ERROR_CODE_BASE + 1000 | Maximum value of the error code range. |
| OH_IPC_USER_ERROR_CODE_MIN = 1909000 | Minimum value of the user-defined error code. |
| OH_IPC_USER_ERROR_CODE_MAX = 1909999 | Maximum value of the user-defined error code. |
