# WebSocket_RequestOptions

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=108aa11c2ceb50c68f8417aa3c60f1dcb55dabdd translatedAt=2026-09-23T01:34:20.237Z pushedAt=2026-09-24T06:00:14.136Z -->

```c
struct WebSocket_RequestOptions {...}
```

## Overview

Defines the parameters for establishing a connection between the WebSocket client and server.

**Since**: 11

**Related module**: [netstack](capi-netstack.md)

**Header file**: [net_websocket_type.h](capi-net-websocket-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| struct [WebSocket_Header](capi-netstack-websocket-header.md) *headers | Pointer to the header information. |
