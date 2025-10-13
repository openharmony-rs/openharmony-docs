# WebSocket_Header

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

## Overview

Defines the header linked list added to the WebSocket client.

**Since**: 11

**Related module**: [netstack](capi-netstack.md)

**Header file**: [net_websocket_type.h](capi-net-websocket-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| const char *fieldName | Header field name.|
| const char *fieldValue | Header field content.|
| struct [WebSocket_Header](capi-netstack-websocket-header.md) *next | Next pointer of the header linked list.|
