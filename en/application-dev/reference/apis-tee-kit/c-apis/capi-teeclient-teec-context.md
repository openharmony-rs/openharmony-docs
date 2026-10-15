# TEEC_Context

```c
typedef struct TEEC_Context {...} TEEC_Context
```

## Overview

Defines the context, a logical connection between a CA and a TEE.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeClient](capi-teeclient.md)

**Header file**: [tee_client_type.h](capi-tee-client-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t fd | File descriptor for the TA. |
| uint8_t *ta_path | Path to the Trusted Application (TA). |
| struct ListNode session_list | Linked list of sessions associated with the context. |
| struct ListNode shrd_mem_list | Linked list of shared memory regions associated with the context. |
| share_buffer->buffer | Pointer to the shared buffer. |
| share_buffer.buffer_barrier | Semaphore for synchronization of the shared buffer. |
| imp | Implementation-specific data. |


