# OH_TrafficFilter_PortMatch

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=8b53200191b48fe20d895cd121b4b62caf228566 translatedAt=2026-09-23T01:41:22.570Z pushedAt=2026-09-24T06:00:14.158Z -->

```c
typedef struct OH_TrafficFilter_PortMatch {...} OH_TrafficFilter_PortMatch
```

## Overview

Defines the port match condition.

**Since:** 26.0.0

**Related module:** [TrafficFilter](capi-trafficfilter.md)

**File to include:** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| [OH_TrafficFilter_PortMatchType](capi-net-trafficfilter-type-h.md#oh_trafficfilter_portmatchtype) type | Match type. |
| bool invert | Whether to invert the match result. The value true means to invert the match result, and false means the opposite. |
| union value | Match rule. (uint16_t single, [OH_TrafficFilter_PortRange](capi-trafficfilter-oh-trafficfilter-portrange.md) range, [OH_TrafficFilter_PortMulti](capi-trafficfilter-oh-trafficfilter-portmulti.md) multi) |


