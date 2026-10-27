# DDK_Ashmem
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=f407beb6a0d69c2cfebf045463efead7e20c4825 translatedAt=2026-10-14T04:35:05.150Z pushedAt=2026-10-19T04:56:12.702Z -->

```c
typedef struct DDK_Ashmem {...} DDK_Ashmem
```

## Overview

Defines the shared memory created by calling [OH_DDK_CreateAshmem](capi-ddk-api-h.md#oh_ddk_createashmem). The buffer of the shared memory provides better performance and is applicable to scenarios that require high-performance data sharing, such as efficient sharing of a large amount of data between multiple modules and fast data exchange between drivers and apps.

**Since**: 12

**Related module**: [Ddk](capi-baseddk.md)

**Header file:** [ddk_types.h](capi-ddk-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t ashmemFd | File descriptor of the shared memory.|
| const uint8_t* address | Buffer address.|
| const uint32_t size | Buffer size.|
| uint32_t offset | Offset of the used buffer. The default value is **0**, indicating that there is no offset and the buffer starts from the address specified by **address**. The sum of **offset** and **bufferLength** cannot exceed **size**. Otherwise, out-of-bounds access occurs. |
| uint32_t bufferLength | Length of the used buffer. By default, the value is equal to **size** (indicating that the entire buffer is used). The sum of **offset** and **bufferLength** cannot be greater than **size**. Otherwise, out-of-bounds access occurs. |
| uint32_t transferredLength | Length of the transferred data, in bytes. This value is updated by the API after data transfer is complete. |


