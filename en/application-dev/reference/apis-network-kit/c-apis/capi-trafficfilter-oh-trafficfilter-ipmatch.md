# OH_TrafficFilter_IPMatch

```c
typedef struct OH_TrafficFilter_IPMatch {...} OH_TrafficFilter_IPMatch
```

## Overview

Defines the IP match condition.

<!--Device-struct OH_TrafficFilter_IPMatch {...}--><!--Device-struct OH_TrafficFilter_IPMatch {...}-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.0

**Related module**: [TrafficFilter](capi-network-kit-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [OH_TrafficFilter_IPMatchType](capi-net-trafficfilter-type-h.md#oh_trafficfilter_ipmatchtype) type | Match type.<br>**Since**: 26.0.0<br><!--Device-OH_TrafficFilter_IPMatchType type--><!--Device-OH_TrafficFilter_IPMatchType type-End--> |
| bool invert | Whether to invert the match result.<br>**Since**: 26.0.0<br><!--Device-bool invert--><!--Device-bool invert-End--> |
| value.single | Single IP address, used when type is OH_TRAFFICFILTER_IP_MATCH_SINGLE<br>**Since**: 26.0.0<br><!--Device-value.single--><!--Device-value.single-End--> |
| value.cidr | CIDR match value, used when type is OH_TRAFFICFILTER_IP_MATCH_CIDR<br>**Since**: 26.0.0<br><!--Device-value.cidr--><!--Device-value.cidr-End--> |
| value.range | IP range match value, used when type is OH_TRAFFICFILTER_IP_MATCH_RANGE<br>**Since**: 26.0.0<br><!--Device-value.range--><!--Device-value.range-End--> |
| value.multi | Multi-IP match value, used when type is OH_TRAFFICFILTER_IP_MATCH_MULTI<br>**Since**: 26.0.0<br><!--Device-value.multi--><!--Device-value.multi-End--> |


