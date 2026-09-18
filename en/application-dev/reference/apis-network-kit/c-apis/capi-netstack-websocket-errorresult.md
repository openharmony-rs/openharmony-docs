# WebSocket_ErrorResult

```c
struct WebSocket_ErrorResult {...}
```

## Overview

Defines the parameters for the connection error received by the WebSocket client.

**Since**: 11

**Related module**: [netstack](capi-netstack.md)

**Header file**: [net_websocket_type.h](capi-net-websocket-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t errorCode | Error code. |
| const char *errorMessage | Error message. |


