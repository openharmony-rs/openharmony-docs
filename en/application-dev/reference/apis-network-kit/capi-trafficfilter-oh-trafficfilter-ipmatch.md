# OH_TrafficFilter_IPMatch

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=7cd2f817688c245414ad83d771260e8515966ace translatedAt=2026-11-04T06:32:24.038Z pushedAt=2026-11-04T08:04:44.848Z nl=1 -->

```c
typedef struct OH_TrafficFilter_IPMatch {...} OH_TrafficFilter_IPMatch
```

## Overview

Defines the IP match condition.

**Since:** 26.0.0

**Related module:** [TrafficFilter](capi-trafficfilter.md)

**File to include:** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| [OH_TrafficFilter_IPMatchType](capi-net-trafficfilter-type-h.md#oh_trafficfilter_ipmatchtype) type | Match type. |
| bool invert | Whether to invert the match result. |
| union value| Match rule. ([OH_TrafficFilter_IPAddress](capi-trafficfilter-oh-trafficfilter-ipaddress.md) single, [OH_TrafficFilter_IPCidr](capi-trafficfilter-oh-trafficfilter-ipcidr.md) cidr, [OH_TrafficFilter_IPRange](capi-trafficfilter-oh-trafficfilter-iprange.md) range, [OH_TrafficFilter_IPMulti](capi-trafficfilter-oh-trafficfilter-ipmulti.md) multi) |


