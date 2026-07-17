# WebSocket_CloseResult

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=66333f405b8ba85b102d9221d24e54901f6cfbf8 translatedAt=2026-06-25T01:49:35.650Z pushedAt=2026-06-26T03:00:41.277Z -->

```c
struct WebSocket_CloseResult {...}
```

## Overview

Defines a struct for parameters received by the WebSocket client when the server closes the connection.

**Since**: 11

**Related module**: [netstack](capi-netstack.md)

**Header file**: [net_websocket_type.h](capi-net-websocket-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t code | Error code.|
| const char *reason | Error cause.|