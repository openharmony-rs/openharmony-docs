# tee_client_constants.h

## Overview

Defines public data and constants.

**Library**: libteec.so

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeClient](capi-tee-kit-teeclient.md)

## Summary

### Enums

| Name | Description |
| -- | -- |
| [TEEC_ReturnCode](#teec_returncode) | Defines the error codes returned. |
| [TEEC_ReturnCodeOrigin](#teec_returncodeorigin) | Defines the sources of the error codes returned. |
| [TEEC_SharedMemCtl](#teec_sharedmemctl) | Defines the identifiers of the shared memory. |
| [TEEC_ParamType](#teec_paramtype) | Defines the parameter types. |
| [TEEC_LoginMethod](#teec_loginmethod) | Defines the login methods. |

### Macros

| Name | Description |
| -- | -- |
| TEEC_PARAM_NUM 4 | Defines the number of <b>TEEC_Parameter</b>s in <b>TEEC_Operation</b>.<br>**Since**: 20 |

## Enum type description

### TEEC_ReturnCode

```c
enum TEEC_ReturnCode
```

**Description**

Defines the error codes returned.

<!--Device-enum TEEC_ReturnCode--><!--Device-enum TEEC_ReturnCode-End-->

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEEC_SUCCESS = 0x0 | The operation is successful.<br><!--Device-TEEC_SUCCESS = 0x0--><!--Device-TEEC_SUCCESS = 0x0-End--> |
| TEEC_ERROR_INVALID_CMD | Invalid command. The command is not supported by the TA.<br><!--Device-TEEC_ERROR_INVALID_CMD--><!--Device-TEEC_ERROR_INVALID_CMD-End--> |
| TEEC_ERROR_SERVICE_NOT_EXIST | The TA does not exist.<br><!--Device-TEEC_ERROR_SERVICE_NOT_EXIST--><!--Device-TEEC_ERROR_SERVICE_NOT_EXIST-End--> |
| TEEC_ERROR_SESSION_NOT_EXIST | The session between the CA and TA does not exist.<br><!--Device-TEEC_ERROR_SESSION_NOT_EXIST--><!--Device-TEEC_ERROR_SESSION_NOT_EXIST-End--> |
| TEEC_ERROR_SESSION_MAXIMUM | The number of connections to the TA has reached the limit.<br><!--Device-TEEC_ERROR_SESSION_MAXIMUM--><!--Device-TEEC_ERROR_SESSION_MAXIMUM-End--> |
| TEEC_ERROR_REGISTER_EXIST_SERVICE | The TA to be registered already exists.<br><!--Device-TEEC_ERROR_REGISTER_EXIST_SERVICE--><!--Device-TEEC_ERROR_REGISTER_EXIST_SERVICE-End--> |
| TEEC_ERROR_TAGET_DEAD_FATAL | Secure OS framework error.<br><!--Device-TEEC_ERROR_TAGET_DEAD_FATAL--><!--Device-TEEC_ERROR_TAGET_DEAD_FATAL-End--> |
| TEEC_ERROR_READ_DATA | Failed to read the file.<br><!--Device-TEEC_ERROR_READ_DATA--><!--Device-TEEC_ERROR_READ_DATA-End--> |
| TEEC_ERROR_WRITE_DATA | Failed to write the file.<br><!--Device-TEEC_ERROR_WRITE_DATA--><!--Device-TEEC_ERROR_WRITE_DATA-End--> |
| TEEC_ERROR_TRUNCATE_OBJECT | Failed to truncate the file.<br><!--Device-TEEC_ERROR_TRUNCATE_OBJECT--><!--Device-TEEC_ERROR_TRUNCATE_OBJECT-End--> |
| TEEC_ERROR_SEEK_DATA | Failed to seek data.<br><!--Device-TEEC_ERROR_SEEK_DATA--><!--Device-TEEC_ERROR_SEEK_DATA-End--> |
| TEEC_ERROR_FSYNC_DATA | File synchronization error.<br><!--Device-TEEC_ERROR_FSYNC_DATA--><!--Device-TEEC_ERROR_FSYNC_DATA-End--> |
| TEEC_ERROR_RENAME_OBJECT | Failed to rename the file.<br><!--Device-TEEC_ERROR_RENAME_OBJECT--><!--Device-TEEC_ERROR_RENAME_OBJECT-End--> |
| TEEC_ERROR_TRUSTED_APP_LOAD_ERROR | Failed to load the TA when opening a session.<br><!--Device-TEEC_ERROR_TRUSTED_APP_LOAD_ERROR--><!--Device-TEEC_ERROR_TRUSTED_APP_LOAD_ERROR-End--> |
| TEEC_ERROR_GENERIC = 0xFFFF0000 | Failed to initialize the TA.<br><!--Device-TEEC_ERROR_GENERIC = 0xFFFF0000--><!--Device-TEEC_ERROR_GENERIC = 0xFFFF0000-End--> |
| TEEC_ERROR_ACCESS_DENIED = 0xFFFF0001 | Permission verification failed. Permission verification is performed before a TEE or session is opened or a command is sent.<br><!--Device-TEEC_ERROR_ACCESS_DENIED = 0xFFFF0001--><!--Device-TEEC_ERROR_ACCESS_DENIED = 0xFFFF0001-End--> |
| TEEC_ERROR_CANCEL = 0xFFFF0002 | The operation is canceled. This error code is returned when you operate the parameter with the cancallation flag.<br><!--Device-TEEC_ERROR_CANCEL = 0xFFFF0002--><!--Device-TEEC_ERROR_CANCEL = 0xFFFF0002-End--> |
| TEEC_ERROR_ACCESS_CONFLICT = 0xFFFF0003 | Concurrent access causes permission conflict. Concurrent access to files in the trusted storage service may cause this error.<br><!--Device-TEEC_ERROR_ACCESS_CONFLICT = 0xFFFF0003--><!--Device-TEEC_ERROR_ACCESS_CONFLICT = 0xFFFF0003-End--> |
| TEEC_ERROR_EXCESS_DATA = 0xFFFF0004 | Too much data is passed in the requested operation for the TA to parse.<br><!--Device-TEEC_ERROR_EXCESS_DATA = 0xFFFF0004--><!--Device-TEEC_ERROR_EXCESS_DATA = 0xFFFF0004-End--> |
| TEEC_ERROR_BAD_FORMAT = 0xFFFF0005 | Incorrect data format. The TA failed to parse the parameters sent from the CA.<br><!--Device-TEEC_ERROR_BAD_FORMAT = 0xFFFF0005--><!--Device-TEEC_ERROR_BAD_FORMAT = 0xFFFF0005-End--> |
| TEEC_ERROR_BAD_PARAMETERS = 0xFFFF0006 | Invalid parameter. The input parameter is null or invalid.<br><!--Device-TEEC_ERROR_BAD_PARAMETERS = 0xFFFF0006--><!--Device-TEEC_ERROR_BAD_PARAMETERS = 0xFFFF0006-End--> |
| TEEC_ERROR_BAD_STATE = 0xFFFF0007 | The operation in the current state is invalid. This error code is returned if the trusted storage service is not initialized when a trusted storage service operation is requested.<br><!--Device-TEEC_ERROR_BAD_STATE = 0xFFFF0007--><!--Device-TEEC_ERROR_BAD_STATE = 0xFFFF0007-End--> |
| TEEC_ERROR_ITEM_NOT_FOUND = 0xFFFF0008 | The requested data is not found.<br><!--Device-TEEC_ERROR_ITEM_NOT_FOUND = 0xFFFF0008--><!--Device-TEEC_ERROR_ITEM_NOT_FOUND = 0xFFFF0008-End--> |
| TEEC_ERROR_NOT_IMPLEMENTED = 0xFFFF0009 | The requested operation has not been implemented yet. This error code is returned when <b>TEEC_RequestCancellation</b> is called.<br><!--Device-TEEC_ERROR_NOT_IMPLEMENTED = 0xFFFF0009--><!--Device-TEEC_ERROR_NOT_IMPLEMENTED = 0xFFFF0009-End--> |
| TEEC_ERROR_NOT_SUPPORTED = 0xFFFF000A | The requested operation is valid but is not supported in this implementation. This error code is returned when certain algorithms of the secure encryption and decryption service, such as DSA, are requested.<br><!--Device-TEEC_ERROR_NOT_SUPPORTED = 0xFFFF000A--><!--Device-TEEC_ERROR_NOT_SUPPORTED = 0xFFFF000A-End--> |
| TEEC_ERROR_NO_DATA = 0xFFFF000B | Expected data for the requested operation is not found.<br><!--Device-TEEC_ERROR_NO_DATA = 0xFFFF000B--><!--Device-TEEC_ERROR_NO_DATA = 0xFFFF000B-End--> |
| TEEC_ERROR_OUT_OF_MEMORY = 0xFFFF000C | The available system resources are insufficient.<br><!--Device-TEEC_ERROR_OUT_OF_MEMORY = 0xFFFF000C--><!--Device-TEEC_ERROR_OUT_OF_MEMORY = 0xFFFF000C-End--> |
| TEEC_ERROR_BUSY = 0xFFFF000D | The system is busy. Some resources are exclusively used by the system.<br><!--Device-TEEC_ERROR_BUSY = 0xFFFF000D--><!--Device-TEEC_ERROR_BUSY = 0xFFFF000D-End--> |
| TEEC_ERROR_COMMUNICATION = 0xFFFF000E | Communication between an application in the REE and a TA failed.<br><!--Device-TEEC_ERROR_COMMUNICATION = 0xFFFF000E--><!--Device-TEEC_ERROR_COMMUNICATION = 0xFFFF000E-End--> |
| TEEC_ERROR_SECURITY = 0xFFFF000F | A security fault is detected in the TEE.<br><!--Device-TEEC_ERROR_SECURITY = 0xFFFF000F--><!--Device-TEEC_ERROR_SECURITY = 0xFFFF000F-End--> |
| TEEC_ERROR_SHORT_BUFFER = 0xFFFF0010 | The supplied buffer is too short for the output generated. This error may occur when {@code TEEC_MEMREF_TEMP_OUTPUT} is used.<br><!--Device-TEEC_ERROR_SHORT_BUFFER = 0xFFFF0010--><!--Device-TEEC_ERROR_SHORT_BUFFER = 0xFFFF0010-End--> |
| TEEC_ERROR_MAC_INVALID = 0xFFFF3071 | MAC value check error.<br><!--Device-TEEC_ERROR_MAC_INVALID = 0xFFFF3071--><!--Device-TEEC_ERROR_MAC_INVALID = 0xFFFF3071-End--> |
| TEEC_ERROR_TARGET_DEAD = 0xFFFF3024 | The TA crashed.<br><!--Device-TEEC_ERROR_TARGET_DEAD = 0xFFFF3024--><!--Device-TEEC_ERROR_TARGET_DEAD = 0xFFFF3024-End--> |
| TEEC_FAIL = 0xFFFF5002 | Common error.<br><!--Device-TEEC_FAIL = 0xFFFF5002--><!--Device-TEEC_FAIL = 0xFFFF5002-End--> |

### TEEC_ReturnCodeOrigin

```c
enum TEEC_ReturnCodeOrigin
```

**Description**

Defines the sources of the error codes returned.

<!--Device-enum TEEC_ReturnCodeOrigin--><!--Device-enum TEEC_ReturnCodeOrigin-End-->

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEEC_ORIGIN_API = 0x1 | The error code indicates an error originated from the client API.<br><!--Device-TEEC_ORIGIN_API = 0x1--><!--Device-TEEC_ORIGIN_API = 0x1-End--> |
| TEEC_ORIGIN_COMMS = 0x2 | The error code indicates an error originated from the communication between the REE and TEE.<br><!--Device-TEEC_ORIGIN_COMMS = 0x2--><!--Device-TEEC_ORIGIN_COMMS = 0x2-End--> |
| TEEC_ORIGIN_TEE = 0x3 | The error code indicates an error originated within the TEE code.<br><!--Device-TEEC_ORIGIN_TEE = 0x3--><!--Device-TEEC_ORIGIN_TEE = 0x3-End--> |
| TEEC_ORIGIN_TRUSTED_APP = 0x4 | The error code indicates an error originated within the TA code.<br><!--Device-TEEC_ORIGIN_TRUSTED_APP = 0x4--><!--Device-TEEC_ORIGIN_TRUSTED_APP = 0x4-End--> |

### TEEC_SharedMemCtl

```c
enum TEEC_SharedMemCtl
```

**Description**

Defines the identifiers of the shared memory.

<!--Device-enum TEEC_SharedMemCtl--><!--Device-enum TEEC_SharedMemCtl-End-->

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEEC_MEM_INPUT = 0x1 | The shared memory can carry data from CAs to TAs.<br><!--Device-TEEC_MEM_INPUT = 0x1--><!--Device-TEEC_MEM_INPUT = 0x1-End--> |
| TEEC_MEM_OUTPUT = 0x2 | The shared memory can carry data from TAs to CAs.<br><!--Device-TEEC_MEM_OUTPUT = 0x2--><!--Device-TEEC_MEM_OUTPUT = 0x2-End--> |
| TEEC_MEM_INOUT = 0x3 | The shared memory can carry data transmitted between CAs and TAs.<br><!--Device-TEEC_MEM_INOUT = 0x3--><!--Device-TEEC_MEM_INOUT = 0x3-End--> |

### TEEC_ParamType

```c
enum TEEC_ParamType
```

**Description**

Defines the parameter types.

<!--Device-enum TEEC_ParamType--><!--Device-enum TEEC_ParamType-End-->

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEEC_NONE = 0x0 | The parameter is not used.<br><!--Device-TEEC_NONE = 0x0--><!--Device-TEEC_NONE = 0x0-End--> |
| TEEC_VALUE_INPUT = 0x01 | The parameter is a {@code TEEC_Value} tagged as input. Data flows from a CA to a TA.<br><!--Device-TEEC_VALUE_INPUT = 0x01--><!--Device-TEEC_VALUE_INPUT = 0x01-End--> |
| TEEC_VALUE_OUTPUT = 0x02 | The parameter is a {@code TEEC_Value} tagged as output. Data flows from a TA to a CA.<br><!--Device-TEEC_VALUE_OUTPUT = 0x02--><!--Device-TEEC_VALUE_OUTPUT = 0x02-End--> |
| TEEC_VALUE_INOUT = 0x03 | The parameter is a {@code TEEC_Value} tagged as both input and output.<br><!--Device-TEEC_VALUE_INOUT = 0x03--><!--Device-TEEC_VALUE_INOUT = 0x03-End--> |
| TEEC_MEMREF_TEMP_INPUT = 0x05 | The parameter is a {@code TEEC_TempMemoryReference} tagged as input. Data flows from a CA to a TA.<br><!--Device-TEEC_MEMREF_TEMP_INPUT = 0x05--><!--Device-TEEC_MEMREF_TEMP_INPUT = 0x05-End--> |
| TEEC_MEMREF_TEMP_OUTPUT = 0x06 | The parameter is a {@code TEEC_TempMemoryReference} tagged as output. Data flows from a TA to a CA.<br><!--Device-TEEC_MEMREF_TEMP_OUTPUT = 0x06--><!--Device-TEEC_MEMREF_TEMP_OUTPUT = 0x06-End--> |
| TEEC_MEMREF_TEMP_INOUT = 0x07 | The parameter is a {@code TEEC_TempMemoryReference} tagged as both input and output. Data is transmitted between a TA and a CA.<br><!--Device-TEEC_MEMREF_TEMP_INOUT = 0x07--><!--Device-TEEC_MEMREF_TEMP_INOUT = 0x07-End--> |
| TEEC_ION_INPUT = 0x08 | The parameter is a {@code TEEC_IonReference} tagged as input. Data flows from a CA to a TA<br><!--Device-TEEC_ION_INPUT = 0x08--><!--Device-TEEC_ION_INPUT = 0x08-End--> |
| TEEC_ION_SGLIST_INPUT = 0x09 | The parameter is a {@code TEEC_IonSglistReference} tagged as input. Data flows from a CA to a TA<br><!--Device-TEEC_ION_SGLIST_INPUT = 0x09--><!--Device-TEEC_ION_SGLIST_INPUT = 0x09-End--> |
| TEEC_MEMREF_WHOLE = 0xc | The parameter is a {@code TEEC_RegisteredMemoryReference} that refers to the entire memory block. The data flow is the same as that of {@code TEEC_SharedMemCtl}.<br><!--Device-TEEC_MEMREF_WHOLE = 0xc--><!--Device-TEEC_MEMREF_WHOLE = 0xc-End--> |
| TEEC_MEMREF_PARTIAL_INPUT = 0xd | The parameter is a {@code TEEC_RegisteredMemoryReference} tagged as input. Data flows from a CA to a TA.<br><!--Device-TEEC_MEMREF_PARTIAL_INPUT = 0xd--><!--Device-TEEC_MEMREF_PARTIAL_INPUT = 0xd-End--> |
| TEEC_MEMREF_PARTIAL_OUTPUT = 0xe | The parameter is a {@code TEEC_RegisteredMemoryReference} tagged as output. Data flows from a TA to a CA.<br><!--Device-TEEC_MEMREF_PARTIAL_OUTPUT = 0xe--><!--Device-TEEC_MEMREF_PARTIAL_OUTPUT = 0xe-End--> |
| TEEC_MEMREF_PARTIAL_INOUT = 0xf | The parameter is a {@code TEEC_RegisteredMemoryReference} tagged as both input and output. Data is transmitted between a TA and a CA.<br><!--Device-TEEC_MEMREF_PARTIAL_INOUT = 0xf--><!--Device-TEEC_MEMREF_PARTIAL_INOUT = 0xf-End--> |

### TEEC_LoginMethod

```c
enum TEEC_LoginMethod
```

**Description**

Defines the login methods.

<!--Device-enum TEEC_LoginMethod--><!--Device-enum TEEC_LoginMethod-End-->

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEEC_LOGIN_PUBLIC = 0x0 | No login data is provided.<br><!--Device-TEEC_LOGIN_PUBLIC = 0x0--><!--Device-TEEC_LOGIN_PUBLIC = 0x0-End--> |
| TEEC_LOGIN_USER | The login data about the user running the CA process is provided.<br><!--Device-TEEC_LOGIN_USER--><!--Device-TEEC_LOGIN_USER-End--> |
| TEEC_LOGIN_GROUP | The login data about the group running the CA process is provided.<br><!--Device-TEEC_LOGIN_GROUP--><!--Device-TEEC_LOGIN_GROUP-End--> |
| TEEC_LOGIN_APPLICATION = 0x4 | The login data about the running CA is provided.<br><!--Device-TEEC_LOGIN_APPLICATION = 0x4--><!--Device-TEEC_LOGIN_APPLICATION = 0x4-End--> |
| TEEC_LOGIN_USER_APPLICATION = 0x5 | The login data about the user running the CA process and about the CA are provided.<br><!--Device-TEEC_LOGIN_USER_APPLICATION = 0x5--><!--Device-TEEC_LOGIN_USER_APPLICATION = 0x5-End--> |
| TEEC_LOGIN_GROUP_APPLICATION = 0x6 | The login data about the group running the CA process and about the CA are provided.<br><!--Device-TEEC_LOGIN_GROUP_APPLICATION = 0x6--><!--Device-TEEC_LOGIN_GROUP_APPLICATION = 0x6-End--> |
| TEEC_LOGIN_IDENTIFY = 0x7 | Login method reserved for TEEOS.<br><!--Device-TEEC_LOGIN_IDENTIFY = 0x7--><!--Device-TEEC_LOGIN_IDENTIFY = 0x7-End--> |


