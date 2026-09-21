# TEEC_UUID

```c
typedef struct TEEC_UUID {...} TEEC_UUID
```

## Overview

Defines the universally unique identifier (UUID) as defined in RFC4122 [2]. The UUIDs are used to identify TAs.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeClient](capi-teeclient.md)

**Header file**: [tee_client_type.h](capi-tee-client-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t timeLow | The low part of the time field. |
| uint16_t timeMid | The middle part of the time field. |
| uint16_t timeHiAndVersion | The high part of the time field and version information. |
| uint8_t clockSeqAndNode[8] | The clock sequence and node field (8 bytes). |


