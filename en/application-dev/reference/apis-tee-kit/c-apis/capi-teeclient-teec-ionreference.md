# TEEC_IonReference

```c
typedef struct TEEC_IonReference {...} TEEC_IonReference
```

## Overview

Describes the size and handle of the ION memory.

**Since**: 20

**Related module**: [TeeClient](capi-teeclient.md)

**Header file**: [tee_client_type.h](capi-tee-client-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int ion_share_fd | File descriptor for the shared ion memory. |
| uint32_t ion_size | Size of the ion memory. |


