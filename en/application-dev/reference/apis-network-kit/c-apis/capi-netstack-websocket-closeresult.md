# WebSocket_CloseResult

```c
struct WebSocket_CloseResult {...}
```

## Overview

Defines the parameters for the connection closure received by the WebSocket client.

<!--Device-struct WebSocket_CloseResult {...}--><!--Device-struct WebSocket_CloseResult {...}-End-->

**System capability**: SystemCapability.Communication.NetStack

**Since**: 11

**Related module**: [netstack](capi-network-kit-netstack.md)

**Header file**: [net_websocket_type.h](capi-net-websocket-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t code | Error code.<br><!--Device-uint32_t code--><!--Device-uint32_t code-End--> |
| const char *reason | Error cause.<br><!--Device-const char *reason--><!--Device-const char *reason-End--> |


