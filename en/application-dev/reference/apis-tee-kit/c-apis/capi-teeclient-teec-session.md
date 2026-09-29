# TEEC_Session

```c
typedef union TEEC_Session {...} TEEC_Session
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
| [struct ListNode](capi-teeclient-listnode.md) head | Linked list head for session-related data. |
| uint64_t imp;
 } | Implementation-specific data. |
| TEEC_Context *context | Pointer to the TEEC context associated with the session. |


