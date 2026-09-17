# WebSocket_CloseOption

```c
struct WebSocket_CloseOption {...}
```

## Overview

Defines the parameters for the proactive connection closure initiated by the WebSocket client.

**Since**: 11

**Related module**: [netstack](capi-netstack.md)

**Header file**: [net_websocket_type.h](capi-net-websocket-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t code | Error code. |
| const char *reason | Error cause. |


