# WebSocket_ErrorResult

```c
struct WebSocket_ErrorResult {...}
```

## Overview

Defines the parameters for the connection error received by the WebSocket client.

<!--Device-struct WebSocket_ErrorResult {...}--><!--Device-struct WebSocket_ErrorResult {...}-End-->

**System capability**: SystemCapability.Communication.NetStack

**Since**: 11

**Related module**: [netstack](capi-network-kit-netstack.md)

**Header file**: [net_websocket_type.h](capi-net-websocket-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t errorCode | Error code.<br><!--Device-uint32_t errorCode--><!--Device-uint32_t errorCode-End--> |
| const char *errorMessage | Error message.<br><!--Device-const char *errorMessage--><!--Device-const char *errorMessage-End--> |


