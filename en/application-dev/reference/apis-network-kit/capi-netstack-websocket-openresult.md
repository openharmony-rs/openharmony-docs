# WebSocket_OpenResult

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=c33290f86c4a896f90eff1ee86d78748f13424d1 translatedAt=2026-09-23T01:33:49.373Z pushedAt=2026-09-24T06:00:14.133Z -->

```c
struct WebSocket_OpenResult {...}
```

## Overview

Defines the parameters returned to the WebSocket client upon successful connection from the server.

**Since**: 11

**Related module**: [netstack](capi-netstack.md)

**Header file**: [net_websocket_type.h](capi-net-websocket-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t code | WebSocket client connection success code. |
| const char *reason | WebSocket client connection success reason. |
