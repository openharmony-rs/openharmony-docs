# OH_TrafficFilter_MACMatch

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=55df9c11d6d7c450cc6d9d1ac7b0b998394459f6 translatedAt=2026-09-23T01:38:06.938Z pushedAt=2026-09-24T06:00:14.149Z -->

```c
typedef struct OH_TrafficFilter_MACMatch {...} OH_TrafficFilter_MACMatch
```

## Overview

Defines the MAC address matching condition.

**Since:** 26.0.1

**Related module:** [TrafficFilter](capi-trafficfilter.md)

**File to include:** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| bool enable | Whether to enable MAC address matching. The value **true** means to enable MAC address matching, and **false** means the opposite. |
| bool invert | Whether to invert the matching result. The value **true** means to invert the matching result, and **false** means the opposite. |
| char srcMac[OH_TRAFFICFILTER_MAC_ADDRSTRLEN] | Source MAC address (in the XX:XX:XX:XX:XX:XX format). |
