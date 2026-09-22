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
| struct [ListNode](capi-teeclient-listnode.md) session_list | Linked list of sessions associated with the context. |
| struct [ListNode](capi-teeclient-listnode.md) shrd_mem_list | Linked list of shared memory regions associated with the context. |
| union | Union for either shared buffer or implementation data.<br>**Since**: 20 |
| struct | Shared buffer used for data exchange and synchronization.<br>**Since**: 20 |
| void *buffer | Pointer to the shared buffer. |
| sem_t buffer_barrier;
 } share_buffer | Semaphore for synchronization of the shared buffer. |
| uint64_t imp;
 } | Implementation-specific data. |


