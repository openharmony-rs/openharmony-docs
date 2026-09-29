# WebSocket_CloseOption

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=c33290f86c4a896f90eff1ee86d78748f13424d1 translatedAt=2026-09-23T01:32:19.223Z pushedAt=2026-09-24T06:00:14.126Z -->

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