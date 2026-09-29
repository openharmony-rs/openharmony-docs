# TEEC_Context

```c
typedef union TEEC_Context {...} TEEC_Context
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
| [](capi-teeclient-listnode.md)s[](capi-teeclient-listnode.md)t[](capi-teeclient-listnode.md)r[](capi-teeclient-listnode.md)u[](capi-teeclient-listnode.md)c[](capi-teeclient-listnode.md)t[](capi-teeclient-listnode.md) | Shared buffer used for data exchange and synchronization.<br>**Since**: 20 |
| void *buffer | Pointer to the shared buffer. |
| sem_t buffer_barrier;
 } share_buffer | Semaphore for synchronization of the shared buffer. |
| uint64_t imp;
 } | Implementation-specific data. |


