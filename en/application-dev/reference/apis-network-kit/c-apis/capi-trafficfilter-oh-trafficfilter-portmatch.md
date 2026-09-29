# OH_TrafficFilter_PortMatch

```c
union OH_TrafficFilter_PortMatch {...}
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
| uint16_t single | Single port, used when type is OH_TRAFFICFILTER_PORT_MATCH_SINGLE<br>**Since**: 26.0.0 |
| [OH_TrafficFilter_PortRange](capi-trafficfilter-oh-trafficfilter-portrange.md) range | Port range match value, used when type is OH_TRAFFICFILTER_PORT_MATCH_RANGE<br>**Since**: 26.0.0 |
| OH_TrafficFilter_PortMulti multi;
 } value | Multi-port match value, used when type is OH_TRAFFICFILTER_PORT_MATCH_MULTI<br>**Since**: 26.0.0 |


