# OH_TrafficFilter_MACMatch

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=7cd2f817688c245414ad83d771260e8515966ace translatedAt=2026-11-04T06:32:55.048Z pushedAt=2026-11-04T08:04:44.851Z nl=1 -->

```c
typedef struct OH_TrafficFilter_MACMatch {...} OH_TrafficFilter_MACMatch
```

## Overview

MAC address matching condition.

**Since:** 26.0.1

**Related module:** [TrafficFilter](capi-trafficfilter.md)

**File to include:** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| bool enable | Whether to enable MAC address matching. The value **true** means to enable MAC address matching, and **false** means not to enable it. |
| bool invert | Whether to invert the matching result. The value **true** means to invert the matching result, and **false** means not to invert it. |
| char srcMac[OH_TRAFFICFILTER_MAC_ADDRSTRLEN] | Source MAC address (in the XX:XX:XX:XX:XX:XX format). |
