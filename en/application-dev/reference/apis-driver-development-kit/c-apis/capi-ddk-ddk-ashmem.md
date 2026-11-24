# DDK_Ashmem

```c
typedef struct DDK_Ashmem {...} DDK_Ashmem
```

## Overview

Defines the shared memory created by calling [OH_DDK_CreateAshmem](capi-ddk-api-h.md#oh_ddk_createashmem). The buffer of the shared memory provides better performance and is applicable to scenarios that require high-performance data sharing, such as efficient sharing of a large amount of data between multiple modules and fast data exchange between drivers and apps.

<!--Device-struct DDK_Ashmem {...}--><!--Device-struct DDK_Ashmem {...}-End-->

**System capability**: SystemCapability.Driver.DDK.Extension

**Since**: 12

**Related module**: [Ddk](capi-driver-development-kit-ddk.md)

**Header file**: [ddk_types.h](capi-ddk-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t ashmemFd | File descriptor of the shared memory.<br><!--Device-int32_t ashmemFd--><!--Device-int32_t ashmemFd-End--> |
| const uint8_t *address | Buffer address.<br><!--Device-const uint8_t *address--><!--Device-const uint8_t *address-End--> |
| const uint32_t size | Buffer size.<br><!--Device-const uint32_t size--><!--Device-const uint32_t size-End--> |
| uint32_t offset | Offset of the used buffer. The default value is **0**, indicating that there is no offset and the buffer starts from the address specified by **address**. The sum of **offset** and **bufferLength** cannot exceed **size**. Otherwise, out-of-bounds access occurs.<br><!--Device-uint32_t offset--><!--Device-uint32_t offset-End--> |
| uint32_t bufferLength | Length of the used buffer. By default, the value is equal to **size** (indicating that the entire buffer is used) . The sum of **offset** and **bufferLength** cannot be greater than **size**. Otherwise, out-of-bounds access occurs.<br><!--Device-uint32_t bufferLength--><!--Device-uint32_t bufferLength-End--> |
| uint32_t transferredLength | Length of the transferred data, in bytes. This value is updated by the API after data transfer is complete.<br><!--Device-uint32_t transferredLength--><!--Device-uint32_t transferredLength-End--> |


