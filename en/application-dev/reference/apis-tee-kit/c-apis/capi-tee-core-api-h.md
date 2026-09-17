# tee_core_api.h

## Overview

Provides APIs for managing trusted application (TA) sessions.

**Library**: NA

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

## Summary

### Macro

| Name | Description |
| -- | -- |
| _TEE_TA_SESSION_HANDLE | Represents the handle for a Trusted Application session.<br>**Since**: 20 |

### Function

| Name | Description |
| -- | -- |
| [void TEE_Panic(TEE_Result panicCode)](#tee_panic) | Raises a panic in the TA instance. |
| [TEE_Result TEE_OpenTASession(const TEE_UUID *destination, uint32_t cancellationRequestTimeout, uint32_t paramTypes, TEE_Param params[TEE_PARAMS_NUM], TEE_TASessionHandle *session, uint32_t *returnOrigin)](#tee_opentasession) | Opens a new session with a TA. |
| [void TEE_CloseTASession(TEE_TASessionHandle session)](#tee_closetasession) | Closes a client session. |
| [TEE_Result TEE_InvokeTACommand(TEE_TASessionHandle session, uint32_t cancellationRequestTimeout, uint32_t commandID, uint32_t paramTypes, TEE_Param params[TEE_PARAMS_NUM], uint32_t *returnOrigin)](#tee_invoketacommand) | Invokes a command in a session opened between this client TA instance and a target TA instance. |

### Variable

| Name | Description |
| -- | -- |
| uint32_t TEE_TASessionHandle | Defines the handle of TA session.<br>**Since**: 20 |

## Function description

### TEE_Panic()

```c
void TEE_Panic(TEE_Result panicCode)
```

**Description**

Raises a panic in the TA instance.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_Result panicCode | Indicates an informative panic code defined by the TA. |

### TEE_OpenTASession()

```c
TEE_Result TEE_OpenTASession(const TEE_UUID *destination, uint32_t cancellationRequestTimeout, uint32_t paramTypes, TEE_Param params[TEE_PARAMS_NUM], TEE_TASessionHandle *session, uint32_t *returnOrigin)
```

**Description**

Opens a new session with a TA.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const TEE_UUID *destination | Indicates the pointer to the <b>TEE_UUID</b> structure that contains the Universal Unique Identifier (UUID) of the target TA. |
| uint32_t cancellationRequestTimeout | Indicates the timeout period in milliseconds or a special value if there is no timeout. |
| uint32_t paramTypes | Indicates the types of all parameters passed in the operation. |
| params | Indicates the parameters passed in the operation. |
| TEE_TASessionHandle *session | Indicates the pointer to the variable that will receive the client session handle. |
| uint32_t *returnOrigin | Indicates the pointer to the variable that holds the return origin. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the session is opened.          Returns <b>TEE_ERROR_ITEM_NOT_FOUND</b> if the TA cannot be found in the Trusted Execution Environment (TEE).          Returns <b>TEE_ERROR_ACCESS_DENIED</b> if the access request to the TA is denied. |

### TEE_CloseTASession()

```c
void TEE_CloseTASession(TEE_TASessionHandle session)
```

**Description**

Closes a client session.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_TASessionHandle session | Indicates the handle of the session to close. |

### TEE_InvokeTACommand()

```c
TEE_Result TEE_InvokeTACommand(TEE_TASessionHandle session, uint32_t cancellationRequestTimeout, uint32_t commandID, uint32_t paramTypes, TEE_Param params[TEE_PARAMS_NUM], uint32_t *returnOrigin)
```

**Description**

Invokes a command in a session opened between this client TA instance and a target TA instance.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_TASessionHandle session | Indicates the handle of the opened session. |
| uint32_t cancellationRequestTimeout | Indicates the timeout period in milliseconds or a special value if there is no timeout. |
| uint32_t commandID | Indicates the identifier of the command to invoke. |
| uint32_t paramTypes | Indicates the types of all parameters passed in the operation. |
| params | Indicates the parameters passed in the operation. |
| uint32_t *returnOrigin | Indicates the pointer to the variable that holds the return origin. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_ACCESS_DENIED</b> if the command fails to be invoked. |


