# OH_TrafficFilter_PortMatch

```c
typedef struct OH_TrafficFilter_PortMatch {...} OH_TrafficFilter_PortMatch
```

## Overview

Defines the port match condition.

<!--Device-struct OH_TrafficFilter_PortMatch {...}--><!--Device-struct OH_TrafficFilter_PortMatch {...}-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.0

**Related module**: [TrafficFilter](capi-network-kit-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [OH_TrafficFilter_PortMatchType](capi-net-trafficfilter-type-h.md#oh_trafficfilter_portmatchtype) type | Match type.<br>**Since**: 26.0.0<br><!--Device-OH_TrafficFilter_PortMatchType type--><!--Device-OH_TrafficFilter_PortMatchType type-End--> |
| bool invert | Whether to invert the match result. The value true means to invert the match result, and false means the opposite.<br>**Since**: 26.0.0<br><!--Device-bool invert--><!--Device-bool invert-End--> |
| value.single | Single port, used when type is OH_TRAFFICFILTER_PORT_MATCH_SINGLE<br>**Since**: 26.0.0<br><!--Device-value.single--><!--Device-value.single-End--> |
| value.range | Port range match value, used when type is OH_TRAFFICFILTER_PORT_MATCH_RANGE<br>**Since**: 26.0.0<br><!--Device-value.range--><!--Device-value.range-End--> |
| value.multi | Multi-port match value, used when type is OH_TRAFFICFILTER_PORT_MATCH_MULTI<br>**Since**: 26.0.0<br><!--Device-value.multi--><!--Device-value.multi-End--> |


