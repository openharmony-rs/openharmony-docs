# TEEC_Session

```c
typedef struct TEEC_Session {...} TEEC_Session
```

## Overview

Defines the session between a CA and a TA.

<!--Device-typedef struct TEEC_Session {...} TEEC_Session--><!--Device-typedef struct TEEC_Session {...} TEEC_Session-End-->

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeClient](capi-tee-kit-teeclient.md)

**Header file**: [tee_client_type.h](capi-tee-client-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t session_id | Session ID for the session. |
| [TEEC_UUID](capi-teeclient-teec-uuid.md) service_id | UUID representing the service associated with the session. |
| uint32_t ops_cnt | The number of operations associated with the session. |
| head | Linked list head for session-related data. |
| imp | Implementation-specific data. |
| [TEEC_Context](capi-teeclient-teec-context.md) *context | Pointer to the TEEC context associated with the session. |


