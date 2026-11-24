# OH_TrafficFilter_PortRange

```c
typedef struct OH_TrafficFilter_PortRange {...} OH_TrafficFilter_PortRange
```

## Overview

Defines the port matching value for range matching.

<!--Device-struct OH_TrafficFilter_PortRange {...}--><!--Device-struct OH_TrafficFilter_PortRange {...}-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.0

**Related module**: [TrafficFilter](capi-network-kit-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint16_t startPort | Start port of the range.<br>**Since**: 26.0.0<br><!--Device-uint16_t startPort--><!--Device-uint16_t startPort-End--> |
| uint16_t endPort | End port of the range.<br>**Since**: 26.0.0<br><!--Device-uint16_t endPort--><!--Device-uint16_t endPort-End--> |


