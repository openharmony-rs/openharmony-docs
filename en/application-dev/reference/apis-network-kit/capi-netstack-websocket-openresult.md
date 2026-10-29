# WebSocket_OpenResult

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=742fd8e7f742ee980eb300ddfd075065ca362dff translatedAt=2026-09-28T01:16:08.009Z pushedAt=2026-10-09T01:46:44.139Z -->

```c
struct WebSocket_OpenResult {...}
```

## Overview

Defines the parameters for the connection success received by the WebSocket client.

**Since**: 11

**Related module**: [netstack](capi-netstack.md)

**Header file**: [net_websocket_type.h](capi-net-websocket-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t code | Result code for successful WebSocket client connection.|
| const char *reason | Reason for successful WebSocket client connection.|
