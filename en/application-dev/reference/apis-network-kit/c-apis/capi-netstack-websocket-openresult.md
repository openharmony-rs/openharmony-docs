# WebSocket_OpenResult

```c
struct WebSocket_OpenResult {...}
```

## Overview

Defines the parameters for the connection success received by the WebSocket client.

<!--Device-struct WebSocket_OpenResult {...}--><!--Device-struct WebSocket_OpenResult {...}-End-->

**System capability**: SystemCapability.Communication.NetStack

**Since**: 11

**Related module**: [netstack](capi-network-kit-netstack.md)

**Header file**: [net_websocket_type.h](capi-net-websocket-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t code | Result code for successful WebSocket client connection. |
| const char *reason | Reason for successful WebSocket client connection. |


