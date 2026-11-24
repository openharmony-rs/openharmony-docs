# Http_PerformanceTiming

```c
typedef struct Http_PerformanceTiming {...} Http_PerformanceTiming
```

## Overview

Defines the HTTP response timing information, which will be collected via [Http_Response](capi-netstack-http-response.md).

<!--Device-struct Http_PerformanceTiming {...}--><!--Device-struct Http_PerformanceTiming {...}-End-->

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

**Related module**: [netstack](capi-network-kit-netstack.md)

**Header file**: [net_http_type.h](capi-net-http-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| double dnsTiming | Duration from the time when the request is initiated to the time when the DNS resolution is complete.<br><!--Device-double dnsTiming--><!--Device-double dnsTiming-End--> |
| double tcpTiming | Duration from the time when the request is initiated to the time when the TCP connection is complete.<br><!--Device-double tcpTiming--><!--Device-double tcpTiming-End--> |
| double tlsTiming | Duration from the time when the request is initiated to the time when the TLS connection is complete.<br><!--Device-double tlsTiming--><!--Device-double tlsTiming-End--> |
| double firstSendTiming | Duration from the time when the request is initiated to the time when the first byte is sent.<br><!--Device-double firstSendTiming--><!--Device-double firstSendTiming-End--> |
| double firstReceiveTiming | Duration from the time when the request is initiated to the time when the first byte is received.<br><!--Device-double firstReceiveTiming--><!--Device-double firstReceiveTiming-End--> |
| double totalFinishTiming | Duration from the time when the request is initiated to the time when the request is complete.<br><!--Device-double totalFinishTiming--><!--Device-double totalFinishTiming-End--> |
| double redirectTiming | Duration from the time when the request is initiated to the time when all redirection steps are complete.<br><!--Device-double redirectTiming--><!--Device-double redirectTiming-End--> |


