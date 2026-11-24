# OH_TrafficFilter_IPMulti

```c
typedef struct OH_TrafficFilter_IPMulti {...} OH_TrafficFilter_IPMulti
```

## Overview

Defines the IP match value for multi-IP matching.

<!--Device-struct OH_TrafficFilter_IPMulti {...}--><!--Device-struct OH_TrafficFilter_IPMulti {...}-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.0

**Related module**: [TrafficFilter](capi-network-kit-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t ipCount | Number of IP addresses in the array.<br>**Since**: 26.0.0<br><!--Device-uint32_t ipCount--><!--Device-uint32_t ipCount-End--> |
| [OH_TrafficFilter_IPAddress](capi-trafficfilter-oh-trafficfilter-ipaddress.md) ips[OH_TRAFFICFILTER_MAX_MULTI_IP_COUNT] | Array of IP addresses.<br>**Since**: 26.0.0<br><!--Device-OH_TrafficFilter_IPAddress ips[OH_TRAFFICFILTER_MAX_MULTI_IP_COUNT]--><!--Device-OH_TrafficFilter_IPAddress ips[OH_TRAFFICFILTER_MAX_MULTI_IP_COUNT]-End--> |


