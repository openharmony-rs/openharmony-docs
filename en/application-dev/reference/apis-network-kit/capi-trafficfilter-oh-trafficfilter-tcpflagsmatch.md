# OH_TrafficFilter_TCPFlagsMatch

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=55df9c11d6d7c450cc6d9d1ac7b0b998394459f6 translatedAt=2026-09-23T01:41:45.309Z pushedAt=2026-09-24T06:00:14.160Z -->

```c
typedef struct OH_TrafficFilter_TCPFlagsMatch {...} OH_TrafficFilter_TCPFlagsMatch
```

## Overview

Defines the TCP flag matching condition. It is valid only for the TCP protocol.

**Since:** 26.0.1

**Related module:** [TrafficFilter](capi-trafficfilter.md)

**File to include:** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| bool enable | Whether to enable TCP flag matching. The value **true** means to enable TCP flag matching, and **false** means not to enable TCP flag matching. |
| uint8_t flagMask | Flag mask (specifies the flags to check). |
| uint8_t flagComp | Flag comparison value (value to compare against the flags). |
