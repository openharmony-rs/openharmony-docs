# OH_TrafficFilter_PortMatch

```c
typedef struct OH_TrafficFilter_PortMatch {...} OH_TrafficFilter_PortMatch
```

## Overview

Port match condition

<!--Device-struct OH_TrafficFilter_PortMatch {...}--><!--Device-struct OH_TrafficFilter_PortMatch {...}-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.0

**Related module**: [TrafficFilter](capi-network-kit-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [OH_TrafficFilter_PortMatchType](capi-net-trafficfilter-type-h.md#oh_trafficfilter_portmatchtype) type | Match type<br>**Since**: 26.0.0 |
| bool invert | Whether to invert the match result<br>**Since**: 26.0.0 |
| value | Match rule<br>**Since**: 26.0.0 |
| value.single | Single port, used when type is OH_TRAFFICFILTER_PORT_MATCH_SINGLE<br>**Since**: 26.0.0 |
| value.range | Port range match value, used when type is OH_TRAFFICFILTER_PORT_MATCH_RANGE<br>**Since**: 26.0.0 |
| value.multi | Multi-port match value, used when type is OH_TRAFFICFILTER_PORT_MATCH_MULTI<br>**Since**: 26.0.0 |


