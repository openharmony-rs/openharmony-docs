# ipc_error_code.h
<!--Kit: IPC Kit-->
<!--Subsystem: Communication-->
<!--Owner: @xdx19211@luodonghui0157-->
<!--Designer: @zhaopeng_gitee-->
<!--Tester: @maxiaorong-->
<!--Adviser: @zhang_yixin13-->

## Overview

Defines the IPC error codes, which are used to identify and handle various errors that may occur during IPC communication. You can quickly locate the cause of an error based on the returned error code, such as parameter error, serialization failure, memory allocation failure, and remote object death, and then take corresponding measures to rectify the error.

**File to include**: <IPCKit/ipc_error_code.h>

**Library**: libipc_capi.so

**System capability**: SystemCapability.Communication.IPC.Core

**Devices supported**: This module applies uniformly across all device types. You can check whether the function is available based on the system capability **SystemCapability.Communication.IPC.Core**.

**Since**: 12

**Related module**: [OHIPCErrorCode](capi-ohipcerrorcode.md)

## Summary

### Enums

| Name| typedef Keyword| Description|
| ---- | ------------- | ---- |
| [OH_IPC_ErrorCode](#oh_ipc_errorcode) | OH_IPC_ErrorCode | Enumerates the IPC error codes.|

## Enum Description

### OH_IPC_ErrorCode

```C
enum OH_IPC_ErrorCode
```

**Description**

Enumerates the IPC error codes.

**Since**: 12

| Value| Description|
| ------ | ---- |
| OH_IPC_SUCCESS = 0 | Execution successful.|
| OH_IPC_ERROR_CODE_BASE = 1901000 | Start error code.|
| OH_IPC_CHECK_PARAM_ERROR = OH_IPC_ERROR_CODE_BASE | Invalid parameter. This error code is returned if the input parameter is a null pointer, the parameter value is out of the valid range, or the parameter type does not match. Check whether the parameter is valid.|
| OH_IPC_PARCEL_WRITE_ERROR = OH_IPC_ERROR_CODE_BASE + 1 | Failed to write data to the serialized object. This error may occur when memory is insufficient during data serialization or the data format is not supported. Check whether the data size and format meet the requirements.|
| OH_IPC_PARCEL_READ_ERROR = OH_IPC_ERROR_CODE_BASE + 2 | Failed to read data from the serialized object. This error may occur when the length of the data to be read exceeds the actual data length or the data format does not match. Check whether the data reading sequence and data format are correct.|
| OH_IPC_MEM_ALLOCATOR_ERROR = OH_IPC_ERROR_CODE_BASE + 3 | Failed to allocate memory. This error code is returned when the system memory is insufficient or the memory allocator is abnormal. Check the memory usage, release unnecessary resources, and try again.|
| OH_IPC_CODE_OUT_OF_RANGE = OH_IPC_ERROR_CODE_BASE + 4 | The command word is out of the value range [0x01, 0x00FFFFFF]. This error code is returned when the command word used for IPC communication is out of the valid range. Check whether the command word meets the specifications.|
| OH_IPC_DEAD_REMOTE_OBJECT = OH_IPC_ERROR_CODE_BASE + 5 | The remote object is dead. This error code is returned when the peer process of IPC communication has exited or the remote object has been destroyed. Re-establish the connection or use an alternative service.|
| OH_IPC_INVALID_USER_ERROR_CODE = OH_IPC_ERROR_CODE_BASE + 6 | The custom error code is out of the range [1909000, 1909999]. This error code is returned when the custom error code is out of the allowed range. Ensure that the custom error code is within the valid range.|
| OH_IPC_INNER_ERROR = OH_IPC_ERROR_CODE_BASE + 7 | IPC internal error. This error code is returned when an unknown error occurs in the IPC system. Record logs and contact technical support or try again later.|
| OH_IPC_ERROR_CODE_MAX = OH_IPC_ERROR_CODE_BASE + 1000 | Maximum error code.|
| OH_IPC_USER_ERROR_CODE_MIN = 1909000 | Minimum value for a custom error code.|
| OH_IPC_USER_ERROR_CODE_MAX = 1909999 | Maximum value for a custom error code.|