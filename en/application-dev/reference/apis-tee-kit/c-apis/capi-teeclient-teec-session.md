# TEEC_Session

```c
typedef struct TEEC_Session {...} TEEC_Session
```

## Overview

Defines the session between a CA and a TA.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeClient](capi-teeclient.md)

**Header file**: [tee_client_type.h](capi-tee-client-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t session_id | Session ID for the session. |
| [TEEC_UUID](capi-teeclient-teec-uuid.md) service_id | UUID representing the service associated with the session. |
| uint32_t ops_cnt | The number of operations associated with the session. |
| union | Union for either a linked list head or implementation-specific data.<br>**Since**: 20 |
| struct [ListNode](capi-teeclient-listnode.md) head | Linked list head for session-related data. |
| uint64_t imp;
 } | Implementation-specific data. |
| [TEEC_Context](capi-teeclient-teec-context.md) *context | Pointer to the TEEC context associated with the session. |


