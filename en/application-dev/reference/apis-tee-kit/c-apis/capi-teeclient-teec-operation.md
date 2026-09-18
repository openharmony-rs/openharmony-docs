# TEEC_Operation

```c
typedef struct TEEC_Operation {...} TEEC_Operation
```

## Overview

Defines the parameters for opening a session or sending a command.

**Since**: 20

**Related module**: [TeeClient](capi-teeclient.md)

**Header file**: [tee_client_type.h](capi-tee-client-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t started | The value 0 means to cancel the command, and other values mean to execute the command. |
| uint32_t paramTypes | Use {@code TEEC_PARAM_TYPES} to create this parameter. |
| [TEEC_Parameter](capi-teeclient-teec-parameter.md) params[TEEC_PARAM_NUM] | Array of parameters for the operation. |
| [TEEC_Session](capi-teeclient-teec-session.md) *session | Pointer to the session associated with the operation. |
| bool cancel_flag | Flag indicating whether the operation is canceled. |


