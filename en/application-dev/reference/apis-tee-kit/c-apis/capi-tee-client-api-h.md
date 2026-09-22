# tee_client_api.h

## Overview

Defines APIs for CAs to access TAs.<br> <p> Example: <p>1. Initialize a TEE: Call <b>TEEC_InitializeContext</b> to initialize the TEE. <p>2. Open a session: Call <b>TEEC_OpenSession</b> with the Universal Unique Identifier (UUID) of the TA. <p>3. Send a command: Call <b>TEEC_InvokeCommand</b> to send a command to the TA. <p>4. Close the session: Call <b>TEEC_CloseSession</b> to close the session. <p>5. Close the TEE: Call <b>TEEC_FinalizeContext</b> to close the TEE.

**Library**: libteec.so

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeClient](capi-teeclient.md)

## Summary

### Macro

| Name | Description |
| -- | -- |
| TEEC_PARAM_TYPES(param0Type, param1Type, param2Type, param3Type)  ((param3Type) << 12 \| (param2Type) << 8 \| (param1Type) << 4 \| (param0Type)) | Defines the values of the parameters transmitted between the REE and TEE.<br>**Since**: 20 |
| TEEC_PARAM_TYPE_GET(paramTypes, index)  (((paramTypes) >> (4*(index))) & 0x0F) | Defines the value of the parameter specified by <b>paramTypes</b> and <b>index</b>.<br>**Since**: 20 |

### Function

| Name | Description |
| -- | -- |
| [TEEC_Result TEEC_InitializeContext(const char *name, TEEC_Context *context)](#teec_initializecontext) | Initializes a TEE.<br> The TEE must be initialized before a session is open or commands are sent. After the initialization, a connection is set up between the CA and the TEE. |
| [void TEEC_FinalizeContext(TEEC_Context *context)](#teec_finalizecontext) | Closes the TEE.<br> After the TEE is closed, the CA is disconnected from the TEE. |
| [TEEC_Result TEEC_OpenSession(TEEC_Context *context, TEEC_Session *session, const TEEC_UUID *destination, uint32_t connectionMethod, const void *connectionData, TEEC_Operation *operation, uint32_t *returnOrigin)](#teec_opensession) | Opens a session.<br> This function is used to set up a connection between the CA and the TA of the specified UUID in the specified TEE context. The data to be transferred is contained in <b>operation</b>. If a session is opened successfully, <b>session</b> is returned providing a description of the connection. If the session fails to open, <b>returnOrigin</b> is returned indicating the cause of the failure. |
| [void TEEC_CloseSession(TEEC_Session *session)](#teec_closesession) | Closes a session.<br> After the session is closed, the CA is disconnected from the TA. |
| [TEEC_Result TEEC_InvokeCommand(TEEC_Session *session, uint32_t commandID, TEEC_Operation *operation, uint32_t *returnOrigin)](#teec_invokecommand) | Sends a command to a TA.<br> The CA sends the command ID to the TA through the specified session. |
| [TEEC_Result TEEC_RegisterSharedMemory(TEEC_Context *context, TEEC_SharedMemory *sharedMem)](#teec_registersharedmemory) | Registers shared memory in the specified TEE context.<br> The registered shared memory can implement zero-copy. The zero-copy function, however, also requires support by the operating system. At present, zero-copy cannot be implemented in this manner. |
| [TEEC_Result TEEC_AllocateSharedMemory(TEEC_Context *context, TEEC_SharedMemory *sharedMem)](#teec_allocatesharedmemory) | Requests shared memory in the specified TEE context.<br> The shared memory can be used to implement zero-copy during data transmission between the REE and TEE. The zero-copy function, however, also requires support by the operating system. At present, zero-copy cannot be implemented in this manner. |
| [void TEEC_ReleaseSharedMemory(TEEC_SharedMemory *sharedMem)](#teec_releasesharedmemory) | Releases the shared memory registered or acquired. |
| [void TEEC_RequestCancellation(TEEC_Operation *operation)](#teec_requestcancellation) | Cancels an operation. |

## Function description

### TEEC_InitializeContext()

```c
TEEC_Result TEEC_InitializeContext(const char *name, TEEC_Context *context)
```

**Description**

Initializes a TEE.<br> The TEE must be initialized before a session is open or commands are sent. After the initialization, a connection is set up between the CA and the TEE.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *name | [IN] Indicates the pointer to the TEE path. |
| TEEC_Context *context | [IN/OUT] Indicates the context pointer, which is the handle of the TEE. |

**Returns**:

| Type | Description |
| -- | -- |
| TEEC_Result | Returns {@code TEEC_SUCCESS} if the TEE is successfully initialized.<br>        Returns {@code TEEC_ERROR_BAD_PARAMETERS} if <b>name</b> is incorrect or <b>context</b> is null.<br>        Returns {@code TEEC_ERROR_GENERIC} if the available system resources are insufficient. |

### TEEC_FinalizeContext()

```c
void TEEC_FinalizeContext(TEEC_Context *context)
```

**Description**

Closes the TEE.<br> After the TEE is closed, the CA is disconnected from the TEE.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEEC_Context *context | [IN/OUT] Indicates the pointer to the TEE that is successfully initialized. |

### TEEC_OpenSession()

```c
TEEC_Result TEEC_OpenSession(TEEC_Context *context, TEEC_Session *session, const TEEC_UUID *destination, uint32_t connectionMethod, const void *connectionData, TEEC_Operation *operation, uint32_t *returnOrigin)
```

**Description**

Opens a session.<br> This function is used to set up a connection between the CA and the TA of the specified UUID in the specified TEE context. The data to be transferred is contained in <b>operation</b>. If a session is opened successfully, <b>session</b> is returned providing a description of the connection. If the session fails to open, <b>returnOrigin</b> is returned indicating the cause of the failure.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEEC_Context *context | [IN/OUT] Indicates the pointer to the TEE that is successfully initialized. |
| TEEC_Session *session | [OUT] Indicates the pointer to the session. The value cannot be null. |
| const TEEC_UUID *destination | [IN] Indicates the pointer to the UUID of the target TA. Each TA has a unique UUID. |
| uint32_t connectionMethod | [IN] Indicates the connection method. For details, see [TEEC_LoginMethod](capi-tee-client-constants-h.md#teec_loginmethod). |
| const void *connectionData | [IN] Indicates the pointer to the connection data, which varies with the connection mode. If the connection mode is {@code TEEC_LOGIN_PUBLIC}, {@code TEEC_LOGIN_USER},<br>{@code TEEC_LOGIN_USER_APPLICATION}, or {@code TEEC_LOGIN_GROUP_APPLICATION}, the connection data must be null.<br>If the connection mode is {@code TEEC_LOGIN_GROUP} or {@code TEEC_LOGIN_GROUP_APPLICATION}, the connection data must point to data of the uint32_t type, which indicates the target group user to be connected by the CA. |
| TEEC_Operation *operation | [IN/OUT] Indicates the pointer to the data to be transmitted between the CA and TA. |
| uint32_t *returnOrigin | [IN/OUT] Indicates the pointer to the error source. For details, see {@code TEEC_ReturnCodeOrigin}. |

**Returns**:

| Type | Description |
| -- | -- |
| TEEC_Result | Returns {@code TEEC_SUCCESS} if the session is open successfully.<br>        Returns {@code TEEC_ERROR_BAD_PARAMETERS} if <b>context</b>, <b>session</b>, or <b>destination</b> is null.<br>        Returns {@code TEEC_ERROR_ACCESS_DENIED} if the access request is denied.<br>        Returns {@code TEEC_ERROR_OUT_OF_MEMORY} if the available system resources are insufficient.<br>        Returns {@code TEEC_ERROR_TRUSTED_APP_LOAD_ERROR} if the TA failed to be loaded.<br>        For details about other return values, see {@code TEEC_ReturnCode}. |

### TEEC_CloseSession()

```c
void TEEC_CloseSession(TEEC_Session *session)
```

**Description**

Closes a session.<br> After the session is closed, the CA is disconnected from the TA.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEEC_Session *session | [IN/OUT] Indicates the pointer to the session to close. |

### TEEC_InvokeCommand()

```c
TEEC_Result TEEC_InvokeCommand(TEEC_Session *session, uint32_t commandID, TEEC_Operation *operation, uint32_t *returnOrigin)
```

**Description**

Sends a command to a TA.<br> The CA sends the command ID to the TA through the specified session.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEEC_Session *session | [IN/OUT] Indicates the pointer to the session opened. |
| uint32_t commandID | [IN] Indicates the command ID supported by the TA. It is defined by the TA. |
| TEEC_Operation *operation | [IN/OUT] Indicates the pointer to the data to be sent from the CA to the TA. |
| uint32_t *returnOrigin | [IN/OUT] Indicates the pointer to the error source. For details, see {@code TEEC_ReturnCodeOrigin}. |

**Returns**:

| Type | Description |
| -- | -- |
| TEEC_Result | Returns {@code TEEC_SUCCESS} if the command is sent successfully.<br>        Returns {@code TEEC_ERROR_BAD_PARAMETERS} if <b>session</b> is null or<br><b>operation</b> is in incorrect format.<br>        Returns {@code TEEC_ERROR_ACCESS_DENIED} if the access request is denied.<br>        Returns {@code TEEC_ERROR_OUT_OF_MEMORY} if the available system resources are insufficient.<br>        For details about other return values, see {@code TEEC_ReturnCode}. |

### TEEC_RegisterSharedMemory()

```c
TEEC_Result TEEC_RegisterSharedMemory(TEEC_Context *context, TEEC_SharedMemory *sharedMem)
```

**Description**

Registers shared memory in the specified TEE context.<br> The registered shared memory can implement zero-copy. The zero-copy function, however, also requires support by the operating system. At present, zero-copy cannot be implemented in this manner.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEEC_Context *context | [IN/OUT] Indicates the pointer to the TEE that is successfully initialized. |
| TEEC_SharedMemory *sharedMem | [IN/OUT] Indicates the pointer to the shared memory. The pointed shared memory cannot be null and the size cannot be 0. |

**Returns**:

| Type | Description |
| -- | -- |
| TEEC_Result | Returns {@code TEEC_SUCCESS} if the operation is successful.<br>        Returns {@code TEEC_ERROR_BAD_PARAMETERS} if <b>context</b> or <b>sharedMem</b> is null or  the pointed memory is empty. |

### TEEC_AllocateSharedMemory()

```c
TEEC_Result TEEC_AllocateSharedMemory(TEEC_Context *context, TEEC_SharedMemory *sharedMem)
```

**Description**

Requests shared memory in the specified TEE context.<br> The shared memory can be used to implement zero-copy during data transmission between the REE and TEE. The zero-copy function, however, also requires support by the operating system. At present, zero-copy cannot be implemented in this manner.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEEC_Context *context | [IN/OUT] Indicates the pointer to the TEE that is successfully initialized. |
| TEEC_SharedMemory *sharedMem | [IN/OUT] Indicates the pointer to the shared memory. The size of the shared memory cannot be 0. |

**Returns**:

| Type | Description |
| -- | -- |
| TEEC_Result | Returns {@code TEEC_SUCCESS} if the operation is successful.<br>        Returns {@code TEEC_ERROR_BAD_PARAMETERS} if <b>context</b> or <b>sharedMem</b> is null.<br>        Returns {@code TEEC_ERROR_OUT_OF_MEMORY} if the available system resources are insufficient. |

### TEEC_ReleaseSharedMemory()

```c
void TEEC_ReleaseSharedMemory(TEEC_SharedMemory *sharedMem)
```

**Description**

Releases the shared memory registered or acquired.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEEC_SharedMemory *sharedMem | [IN/OUT] Indicates the pointer to the shared memory to release. |

### TEEC_RequestCancellation()

```c
void TEEC_RequestCancellation(TEEC_Operation *operation)
```

**Description**

Cancels an operation.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEEC_Operation *operation | [IN/OUT] Indicates the pointer to the data to be sent from the CA to the TA. |


