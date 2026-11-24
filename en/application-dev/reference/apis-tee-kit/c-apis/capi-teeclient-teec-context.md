# TEEC_Context

```c
typedef struct TEEC_Context {...} TEEC_Context
```

## Overview

Defines the context, a logical connection between a CA and a TEE.

<!--Device-typedef struct TEEC_Context {...} TEEC_Context--><!--Device-typedef struct TEEC_Context {...} TEEC_Context-End-->

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeClient](capi-tee-kit-teeclient.md)

**Header file**: [tee_client_type.h](capi-tee-client-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t fd | File descriptor for the TA.<br><!--Device-int32_t fd--><!--Device-int32_t fd-End--> |
| uint8_t *ta_path | Path to the Trusted Application (TA).<br><!--Device-uint8_t *ta_path--><!--Device-uint8_t *ta_path-End--> |
| [struct ListNode](capi-teeclient-listnode.md) session_list | Linked list of sessions associated with the context.<br><!--Device-struct ListNode session_list--><!--Device-struct ListNode session_list-End--> |
| [struct ListNode](capi-teeclient-listnode.md) shrd_mem_list | Linked list of shared memory regions associated with the context.<br><!--Device-struct ListNode shrd_mem_list--><!--Device-struct ListNode shrd_mem_list-End--> |
| share_buffer.buffer | Pointer to the shared buffer.<br><!--Device-share_buffer.buffer--><!--Device-share_buffer.buffer-End--> |
| share_buffer.buffer_barrier | Semaphore for synchronization of the shared buffer.<br><!--Device-share_buffer.buffer_barrier--><!--Device-share_buffer.buffer_barrier-End--> |
| imp | Implementation-specific data.<br><!--Device-imp--><!--Device-imp-End--> |


