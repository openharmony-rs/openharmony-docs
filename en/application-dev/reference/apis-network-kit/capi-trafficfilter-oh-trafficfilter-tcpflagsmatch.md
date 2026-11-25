# OH_TrafficFilter_TCPFlagsMatch

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=7cd2f817688c245414ad83d771260e8515966ace translatedAt=2026-11-04T06:35:14.859Z pushedAt=2026-11-04T08:04:44.864Z nl=1 -->

```c
typedef struct OH_TrafficFilter_TCPFlagsMatch {...} OH_TrafficFilter_TCPFlagsMatch
```

## Overview

TCP flag matching condition. Valid only for the TCP protocol.

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
