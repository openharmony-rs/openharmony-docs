# Http_PerformanceTiming
<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=6bea3977f519f83af05e3810eb42fedb6ffc4399 translatedAt=2026-09-28T01:13:03.612Z pushedAt=2026-10-09T01:40:10.487Z -->

```c
typedef struct Http_PerformanceTiming {...} Http_PerformanceTiming
```

## Overview

Defines the HTTP response timing information, which will be collected via [Http_Response](capi-netstack-http-response.md#member-variables).

**Since**: 20

**Related module**: [netstack](capi-netstack.md)

**Header file**: [net_http_type.h](capi-net-http-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| double dnsTiming | Time elapsed from the request to the completion of DNS resolution, including domain name resolution and TCP connection. Unit: ms. |
| double tcpTiming | Time elapsed from the request to the completion of the TCP connection. Unit: ms. |
| double tlsTiming | Time elapsed from the request to the completion of the TLS connection. Unit: ms. |
| double firstSendTiming | Time elapsed from the request to the start of sending the first byte. Unit: ms. |
| double firstReceiveTiming | Time elapsed from the request to the receipt of the first byte. Unit: ms. |
| double totalFinishTiming | Time elapsed from the request to the completion of the request. Unit: ms. |
| double redirectTiming | Time elapsed from the request to the completion of all redirect steps. Unit: ms. |


