# tee_uuid

```c
typedef struct tee_uuid {...} TEE_UUID
```

## Overview

Defines an UUID of TA.

<!--Device-struct tee_uuid {...}--><!--Device-struct tee_uuid {...}-End-->

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-tee-kit-teetrusted.md)

**Header file**: [tee_defines.h](capi-tee-defines-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t timeLow | Low part of the UUID time.<br><!--Device-uint32_t timeLow--><!--Device-uint32_t timeLow-End--> |
| uint16_t timeMid | Mid part of the UUID time.<br><!--Device-uint16_t timeMid--><!--Device-uint16_t timeMid-End--> |
| uint16_t timeHiAndVersion | High part of the UUID time and version.<br><!--Device-uint16_t timeHiAndVersion--><!--Device-uint16_t timeHiAndVersion-End--> |
| uint8_t clockSeqAndNode[NODE_LEN] | Clock sequence and node of the UUID.<br><!--Device-uint8_t clockSeqAndNode[NODE_LEN]--><!--Device-uint8_t clockSeqAndNode[NODE_LEN]-End--> |


