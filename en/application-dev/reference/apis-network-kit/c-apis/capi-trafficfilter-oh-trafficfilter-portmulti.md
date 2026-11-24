# OH_TrafficFilter_PortMulti

```c
typedef struct OH_TrafficFilter_PortMulti {...} OH_TrafficFilter_PortMulti
```

## Overview

Defines the port matching value for multi-port matching.

<!--Device-struct OH_TrafficFilter_PortMulti {...}--><!--Device-struct OH_TrafficFilter_PortMulti {...}-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.0

**Related module**: [TrafficFilter](capi-network-kit-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t portCount | Number of ports in the array.<br>**Since**: 26.0.0<br><!--Device-uint32_t portCount--><!--Device-uint32_t portCount-End--> |
| uint16_t ports[OH_TRAFFICFILTER_MAX_MULTI_PORT_COUNT] | Port array.<br>**Since**: 26.0.0<br><!--Device-uint16_t ports[OH_TRAFFICFILTER_MAX_MULTI_PORT_COUNT]--><!--Device-uint16_t ports[OH_TRAFFICFILTER_MAX_MULTI_PORT_COUNT]-End--> |


