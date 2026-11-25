# OH_TrafficFilter_PacketCopyMode

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=7cd2f817688c245414ad83d771260e8515966ace translatedAt=2026-11-04T06:34:12.121Z pushedAt=2026-11-04T08:04:44.857Z nl=1 -->

```c
typedef enum OH_TrafficFilter_PacketCopyMode {...} OH_TrafficFilter_PacketCopyMode
```

## Overview

Enumerates the packet copy modes.

**Since:** 26.0.1

**Related module:** [TrafficFilter](capi-trafficfilter.md)

**File to include:** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Value

| Name | Description |
| -- | -- |
| OH_TRAFFICFILTER_COPY_MODE_META = 0 | Copies only the metadata (without copying the packet data). |
| OH_TRAFFICFILTER_COPY_MODE_HEADER = 1 | Copies only the packet header (specified by packetCopyLen). |
| OH_TRAFFICFILTER_COPY_MODE_FULL = 2 | Copies the entire packet. |
| OH_TRAFFICFILTER_COPY_MODE_MAXLEN = 3 | Copies the packet of the specified maximum length. |
