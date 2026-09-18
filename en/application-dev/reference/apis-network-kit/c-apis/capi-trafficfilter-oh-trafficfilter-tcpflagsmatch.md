# OH_TrafficFilter_TCPFlagsMatch

```c
typedef struct OH_TrafficFilter_TCPFlagsMatch {...} OH_TrafficFilter_TCPFlagsMatch
```

## Overview

TCP flags match condition<br> Matches TCP packets based on TCP flag settings

**Since**: 26.1.0

**Related module**: [TrafficFilter](capi-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| bool enable | Enable TCP flags matching<br>**Since**: 26.1.0 |
| uint8_t flagMask | Flag mask (which flags to check, use OH_TRAFFICFILTER_TCP_FLAG_* constants)<br>**Since**: 26.1.0 |
| uint8_t flagComp | Flag to compare (which flags must be set)<br>**Since**: 26.1.0 |


