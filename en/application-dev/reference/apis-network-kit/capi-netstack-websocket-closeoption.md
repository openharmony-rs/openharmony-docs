# WebSocket_CloseOption

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=742fd8e7f742ee980eb300ddfd075065ca362dff translatedAt=2026-09-28T01:14:09.090Z pushedAt=2026-10-09T01:44:48.675Z -->

```c
struct WebSocket_CloseOption {...}
```

## Overview

Defines the parameters for proactively closing a WebSocket client connection.

**Since**: 11

**Related module**: [netstack](capi-netstack.md)

**Header file**: [net_websocket_type.h](capi-net-websocket-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t code | Error code.|
| const char *reason | Error cause.|