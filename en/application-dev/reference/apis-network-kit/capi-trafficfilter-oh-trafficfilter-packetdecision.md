# OH_TrafficFilter_PacketDecision

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=55df9c11d6d7c450cc6d9d1ac7b0b998394459f6 translatedAt=2026-09-23T01:39:50.156Z pushedAt=2026-09-24T06:00:14.154Z -->

```c
typedef enum OH_TrafficFilter_PacketDecision {...} OH_TrafficFilter_PacketDecision
```

## Overview

Enumerates the packet processing decision types.

**Since:** 26.0.1

**Related module:** [TrafficFilter](capi-trafficfilter.md)

**File to include:** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Enum Item

| Name | Description |
| -- | -- |
| OH_TRAFFICFILTER_DECISION_ACCEPT = 0 | Accepts the packet. |
| OH_TRAFFICFILTER_DECISION_DROP | Drops the packet. |
