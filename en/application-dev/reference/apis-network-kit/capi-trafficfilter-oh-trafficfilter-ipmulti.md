# OH_TrafficFilter_IPMulti

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=a5af4ad1c04839519f112b110b49ed35699b6607 translatedAt=2026-09-23T01:37:52.455Z pushedAt=2026-09-24T06:00:14.147Z -->

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


