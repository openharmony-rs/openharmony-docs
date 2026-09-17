# OH_TrafficFilter_PortMulti

```c
typedef struct OH_TrafficFilter_PortMulti {...} OH_TrafficFilter_PortMulti
```

## Overview

Port match value for multi-port match

**Since**: 26.0.0

**Related module**: [TrafficFilter](capi-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t portCount | Number of ports in the array<br>**Since**: 26.0.0 |
| uint16_t ports[OH_TRAFFICFILTER_MAX_MULTI_PORT_COUNT] | Port array<br>**Since**: 26.0.0 |


