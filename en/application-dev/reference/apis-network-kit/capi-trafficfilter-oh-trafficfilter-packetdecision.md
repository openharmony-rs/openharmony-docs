# OH_TrafficFilter_PacketDecision

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=7cd2f817688c245414ad83d771260e8515966ace translatedAt=2026-11-04T06:34:04.544Z pushedAt=2026-11-04T08:04:44.858Z nl=1 -->

```c
typedef enum OH_TrafficFilter_PacketDecision {...} OH_TrafficFilter_PacketDecision
```

## Overview

Enumerates the packet processing decision types.

**Since:** 26.0.1

**Related module:** [TrafficFilter](capi-trafficfilter.md)

**File to include:** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Value

| Name | Description |
| -- | -- |
| OH_TRAFFICFILTER_DECISION_ACCEPT = 0 | Accepts the packet. |
| OH_TRAFFICFILTER_DECISION_DROP | Drops the packet. |
