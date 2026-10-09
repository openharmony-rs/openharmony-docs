# WebSocket_ErrorResult

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=742fd8e7f742ee980eb300ddfd075065ca362dff translatedAt=2026-09-28T01:14:42.836Z pushedAt=2026-10-09T01:45:03.337Z -->

```c
struct WebSocket_ErrorResult {...}
```

## Overview

Defines the parameters of the connection error from the server for the WebSocket client.

**Since**: 11

**Related module**: [netstack](capi-netstack.md)

**Header file**: [net_websocket_type.h](capi-net-websocket-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t errorCode | Error code.|
| const char *errorMessage | Error message.|
