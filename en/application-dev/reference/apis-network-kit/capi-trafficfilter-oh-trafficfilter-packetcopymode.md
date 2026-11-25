# OH_TrafficFilter_PacketCopyMode

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=55df9c11d6d7c450cc6d9d1ac7b0b998394459f6 translatedAt=2026-09-23T01:39:58.313Z pushedAt=2026-09-24T06:00:14.155Z -->

```c
typedef enum OH_TrafficFilter_PacketCopyMode {...} OH_TrafficFilter_PacketCopyMode
```

## Overview

Enumerates the packet copy modes.

**Since:** 26.0.1

**Related module:** [TrafficFilter](capi-trafficfilter.md)

**File to include:** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Enum Item

| Name | Description |
| -- | -- |
| OH_TRAFFICFILTER_COPY_MODE_META = 0 | Copies only the metadata (without the packet data). |
| OH_TRAFFICFILTER_COPY_MODE_HEADER = 1 | Copies only the packet header (specified by packetCopyLen). |
| OH_TRAFFICFILTER_COPY_MODE_FULL = 2 | Copies the entire packet. |
| OH_TRAFFICFILTER_COPY_MODE_MAXLEN = 3 | Copies the packet of the specified maximum length. |
