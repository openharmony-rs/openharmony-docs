# OH_TrafficFilter_ConntrackMatch

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=55df9c11d6d7c450cc6d9d1ac7b0b998394459f6 translatedAt=2026-09-23T01:36:11.573Z pushedAt=2026-09-24T06:00:14.142Z -->

```c
typedef struct OH_TrafficFilter_ConntrackMatch {...} OH_TrafficFilter_ConntrackMatch
```

## Overview

Defines the connection tracking match condition.

**Since:** 26.0.1

**Related module:** [TrafficFilter](capi-trafficfilter.md)

**File to include:** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| bool enable | Whether to enable connection tracking match. The value **true** means to enable connection tracking match, and **false** means not to enable it. |
| uint8_t stateMask | Connection state. |