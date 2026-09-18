# Http_PerformanceTiming

```c
typedef struct Http_PerformanceTiming {...} Http_PerformanceTiming
```

## Overview

Defines the HTTP response timing information, which will be collected via [Http_Response](capi-netstack-http-response.md).

**Since**: 20

**Related module**: [netstack](capi-netstack.md)

**Header file**: [net_http_type.h](capi-net-http-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| double dnsTiming | Duration from the time when the request is initiated to the time when the DNS resolution is complete. |
| double tcpTiming | Duration from the time when the request is initiated to the time when the TCP connection is complete. |
| double tlsTiming | Duration from the time when the request is initiated to the time when the TLS connection is complete. |
| double firstSendTiming | Duration from the time when the request is initiated to the time when the first byte is sent. |
| double firstReceiveTiming | Duration from the time when the request is initiated to the time when the first byte is received. |
| double totalFinishTiming | Duration from the time when the request is initiated to the time when the request is complete. |
| double redirectTiming | Duration from the time when the request is initiated to the time when all redirection steps are complete. |


