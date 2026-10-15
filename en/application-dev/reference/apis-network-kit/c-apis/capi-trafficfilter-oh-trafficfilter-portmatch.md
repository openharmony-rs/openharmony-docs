# OH_TrafficFilter_PortMatch

```c
struct OH_TrafficFilter_PortMatch {...}
```

## Overview

Port match condition

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.0

**Related module**: [TrafficFilter](capi-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| OH_TrafficFilter_PortMatchType type | Match type<br>**Since**: 26.0.0 |
| bool invert | Whether to invert the match result<br>**Since**: 26.0.0 |
| value.single | Single port, used when type is OH_TRAFFICFILTER_PORT_MATCH_SINGLE<br>**Since**: 26.0.0 |
| value.range | Port range match value, used when type is OH_TRAFFICFILTER_PORT_MATCH_RANGE<br>**Since**: 26.0.0 |
| value.multi | Multi-port match value, used when type is OH_TRAFFICFILTER_PORT_MATCH_MULTI<br>**Since**: 26.0.0 |


