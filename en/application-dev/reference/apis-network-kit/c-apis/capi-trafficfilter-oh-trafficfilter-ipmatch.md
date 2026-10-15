# OH_TrafficFilter_IPMatch

```c
struct OH_TrafficFilter_IPMatch {...}
```

## Overview

IP match condition

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.0

**Related module**: [TrafficFilter](capi-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| OH_TrafficFilter_IPMatchType type | Match type<br>**Since**: 26.0.0 |
| bool invert | Whether to invert the match result<br>**Since**: 26.0.0 |
| value.single | Single IP address, used when type is OH_TRAFFICFILTER_IP_MATCH_SINGLE<br>**Since**: 26.0.0 |
| value.cidr | CIDR match value, used when type is OH_TRAFFICFILTER_IP_MATCH_CIDR<br>**Since**: 26.0.0 |
| value.range | IP range match value, used when type is OH_TRAFFICFILTER_IP_MATCH_RANGE<br>**Since**: 26.0.0 |
| value.multi | Multi-IP match value, used when type is OH_TRAFFICFILTER_IP_MATCH_MULTI<br>**Since**: 26.0.0 |


