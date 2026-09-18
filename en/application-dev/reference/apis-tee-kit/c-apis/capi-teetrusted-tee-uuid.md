# tee_uuid

```c
typedef struct tee_uuid {...} TEE_UUID
```

## Overview

Defines an UUID of TA.

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

**Header file**: [tee_defines.h](capi-tee-defines-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t timeLow | Low part of the UUID time. |
| uint16_t timeMid | Mid part of the UUID time. |
| uint16_t timeHiAndVersion | High part of the UUID time and version. |
| uint8_t clockSeqAndNode[NODE_LEN] | Clock sequence and node of the UUID. |


