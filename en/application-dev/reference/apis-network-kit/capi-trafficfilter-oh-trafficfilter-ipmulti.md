# OH_TrafficFilter_IPMulti

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=2d04c102eeb6382287f6c041f48409f3f929ce06 translatedAt=2026-09-28T01:16:51.741Z pushedAt=2026-10-09T02:15:46.123Z -->

```c
typedef struct OH_TrafficFilter_IPMulti {...} OH_TrafficFilter_IPMulti
```

## Overview

Defines the IP match value for multi-IP matching.

**Since:** 26.0.0

**Related module:** [TrafficFilter](capi-trafficfilter.md)

**Header file:** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| uint32_t ipCount | Number of IP addresses in the array. |
| [OH_TrafficFilter_IPAddress](capi-trafficfilter-oh-trafficfilter-ipaddress.md) ips[OH_TRAFFICFILTER_MAX_MULTI_IP_COUNT] | Array of IP addresses. |


