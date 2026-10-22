# OH_TrafficFilter_PacketCallback

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=55df9c11d6d7c450cc6d9d1ac7b0b998394459f6 translatedAt=2026-09-23T01:38:50.245Z pushedAt=2026-09-24T06:00:14.151Z -->

```c
typedef OH_TrafficFilter_PacketDecision (*OH_TrafficFilter_PacketCallback)(
    const OH_TrafficFilter_PacketDesc* packet,
    void* userData
)
```

## Overview

Defines the packet callback type.

**Since:** 26.0.1

**Related module:** [TrafficFilter](capi-trafficfilter.md)

**File to include:** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Parameters

| Name | Description |
| -- | -- |
| [const OH_TrafficFilter_PacketDesc](capi-trafficfilter-oh-trafficfilter-packetdesc.md)* packet | Pointer to the packet descriptor. |
| void* userData | Pointer to the user data. |

### Return

| Type | Description |
| -- | -- |
| [OH_TrafficFilter_PacketDecision](capi-trafficfilter-oh-trafficfilter-packetdecision.md) | Packet processing decision (accept or discard). |
