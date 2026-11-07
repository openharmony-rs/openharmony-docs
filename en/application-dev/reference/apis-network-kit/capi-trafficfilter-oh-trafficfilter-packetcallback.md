# OH_TrafficFilter_PacketCallback

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=7cd2f817688c245414ad83d771260e8515966ace translatedAt=2026-11-04T06:33:00.407Z pushedAt=2026-11-04T08:04:44.853Z nl=1 -->

```c
typedef OH_TrafficFilter_PacketDecision (*OH_TrafficFilter_PacketCallback)(
    const OH_TrafficFilter_PacketDesc* packet,
    void* userData
)
```

## Overview

Defines a pointer to the packet callback.

**Since:** 26.0.1

**Related module:** [TrafficFilter](capi-trafficfilter.md)

**File to include:** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Parameters

| Name | Description |
| -- | -- |
| [const OH_TrafficFilter_PacketDesc](capi-trafficfilter-oh-trafficfilter-packetdesc.md)* packet | Pointer to the packet descriptor. |
| void* userData | User data. |

### Back

| Type | Description |
| -- | -- |
| [OH_TrafficFilter_PacketDecision](capi-trafficfilter-oh-trafficfilter-packetdecision.md) | Packet processing decision (accept or discard). |
