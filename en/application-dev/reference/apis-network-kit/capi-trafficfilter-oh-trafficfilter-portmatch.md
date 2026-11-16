# OH_TrafficFilter_PortMatch

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=7cd2f817688c245414ad83d771260e8515966ace translatedAt=2026-11-04T06:34:43.018Z pushedAt=2026-11-04T08:04:44.860Z nl=1 -->

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
| [OH_TrafficFilter_PortMatchType](capi-net-trafficfilter-type-h.md#oh_trafficfilter_portmatchtype) type | Match type.<br>**Since:** 26.0.0 |
| bool invert | Whether to invert the match result. The value **true** means to invert the match result, and **false** means not to invert the match result.<br>**Since:** 26.0.0 |
| union value| Matching rule. (uint16_t single, [OH_TrafficFilter_PortRange](capi-trafficfilter-oh-trafficfilter-portrange.md) range, [OH_TrafficFilter_PortMulti](capi-trafficfilter-oh-trafficfilter-portmulti.md) multi)|


