# OH_TrafficFilter_IPMulti

```c
typedef struct OH_TrafficFilter_IPMulti {...} OH_TrafficFilter_IPMulti
```

## Overview

IP match value for multi-IP match

**Since**: 26.0.0

**Related module**: [TrafficFilter](capi-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t ipCount | Number of IP addresses in the array<br>**Since**: 26.0.0 |
| [OH_TrafficFilter_IPAddress](capi-trafficfilter-oh-trafficfilter-ipaddress.md) ips[OH_TRAFFICFILTER_MAX_MULTI_IP_COUNT] | IP address array<br>**Since**: 26.0.0 |


