# WebSocket_Header

```c
struct WebSocket_Header {...}
```

## Overview

Defines the header linked list added to the WebSocket client.

<!--Device-struct WebSocket_Header {...}--><!--Device-struct WebSocket_Header {...}-End-->

**System capability**: SystemCapability.Communication.NetStack

**Since**: 11

**Related module**: [netstack](capi-network-kit-netstack.md)

**Header file**: [net_websocket_type.h](capi-net-websocket-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char *fieldName | Pointer to the field name of a header. |
| const char *fieldValue | Pointer to the field value of a header. |
| [struct WebSocket_Header](capi-netstack-websocket-header.md) *next | Next pointer of the header linked list. |


