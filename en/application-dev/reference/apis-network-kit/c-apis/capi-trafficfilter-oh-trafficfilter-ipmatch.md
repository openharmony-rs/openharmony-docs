# OH_TrafficFilter_IPMatch

```c
typedef struct OH_TrafficFilter_IPMatch {...} OH_TrafficFilter_IPMatch
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
| [OH_TrafficFilter_IPMatchType](capi-net-trafficfilter-type-h.md#oh_trafficfilter_ipmatchtype) type | Match type<br>**Since**: 26.0.0 |
| bool invert | Whether to invert the match result<br>**Since**: 26.0.0 |
| union | Match rule<br>**Since**: 26.0.0 |
| [OH_TrafficFilter_IPAddress](capi-trafficfilter-oh-trafficfilter-ipaddress.md) single | Single IP address, used when type is OH_TRAFFICFILTER_IP_MATCH_SINGLE<br>**Since**: 26.0.0 |
| [OH_TrafficFilter_IPCidr](capi-trafficfilter-oh-trafficfilter-ipcidr.md) cidr | CIDR match value, used when type is OH_TRAFFICFILTER_IP_MATCH_CIDR<br>**Since**: 26.0.0 |
| [OH_TrafficFilter_IPRange](capi-trafficfilter-oh-trafficfilter-iprange.md) range | IP range match value, used when type is OH_TRAFFICFILTER_IP_MATCH_RANGE<br>**Since**: 26.0.0 |
| OH_TrafficFilter_IPMulti multi;
 } value | Multi-IP match value, used when type is OH_TRAFFICFILTER_IP_MATCH_MULTI<br>**Since**: 26.0.0 |


