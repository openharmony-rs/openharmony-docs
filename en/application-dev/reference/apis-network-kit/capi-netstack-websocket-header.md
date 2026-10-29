# WebSocket_Header

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=742fd8e7f742ee980eb300ddfd075065ca362dff translatedAt=2026-09-28T01:15:06.693Z pushedAt=2026-10-09T01:45:24.746Z -->

```c
struct WebSocket_Header {...}
```

## Overview

Defines the linked list node for adding a header to the WebSocket client.

**Since**: 11

**Related module**: [netstack](capi-netstack.md)

**Header file**: [net_websocket_type.h](capi-net-websocket-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| const char *fieldName | Pointer to the field name of a header.|
| const char *fieldValue | Pointer to the field value of a header.|
| struct [WebSocket_Header](capi-netstack-websocket-header.md) *next | Next pointer to the header linked list.|
