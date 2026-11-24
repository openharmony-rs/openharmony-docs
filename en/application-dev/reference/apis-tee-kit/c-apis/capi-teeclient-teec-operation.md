# TEEC_Operation

```c
typedef struct TEEC_Operation {...} TEEC_Operation
```

## Overview

Defines the parameters for opening a session or sending a command.

<!--Device-typedef struct TEEC_Operation {...} TEEC_Operation--><!--Device-typedef struct TEEC_Operation {...} TEEC_Operation-End-->

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeClient](capi-tee-kit-teeclient.md)

**Header file**: [tee_client_type.h](capi-tee-client-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t started | The value 0 means to cancel the command, and other values mean to execute the command.<br><!--Device-uint32_t started--><!--Device-uint32_t started-End--> |
| uint32_t paramTypes | Use {@code TEEC_PARAM_TYPES} to create this parameter.<br><!--Device-uint32_t paramTypes--><!--Device-uint32_t paramTypes-End--> |
| [TEEC_Parameter](capi-teeclient-teec-parameter.md) params[TEEC_PARAM_NUM] | Array of parameters for the operation.<br><!--Device-TEEC_Parameter params[TEEC_PARAM_NUM]--><!--Device-TEEC_Parameter params[TEEC_PARAM_NUM]-End--> |
| [TEEC_Session](capi-teeclient-teec-session.md) *session | Pointer to the session associated with the operation.<br><!--Device-TEEC_Session *session--><!--Device-TEEC_Session *session-End--> |
| bool cancel_flag | Flag indicating whether the operation is canceled.<br><!--Device-bool cancel_flag--><!--Device-bool cancel_flag-End--> |


