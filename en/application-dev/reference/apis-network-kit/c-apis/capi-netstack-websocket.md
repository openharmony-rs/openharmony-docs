# WebSocket

```c
struct WebSocket {...}
```

## Overview

Defines the struct of the WebSocket client.

<!--Device-struct WebSocket {...}--><!--Device-struct WebSocket {...}-End-->

**System capability**: SystemCapability.Communication.NetStack

**Since**: 11

**Related module**: [netstack](capi-network-kit-netstack.md)

**Header file**: [net_websocket_type.h](capi-net-websocket-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [WebSocket_OnOpenCallback](capi-net-websocket-type-h.md#websocket_onopencallback) onOpen | Pointer to the callback invoked when the WebSocket client receives a connection message.<br><!--Device-WebSocket_OnOpenCallback onOpen--><!--Device-WebSocket_OnOpenCallback onOpen-End--> |
| [WebSocket_OnMessageCallback](capi-net-websocket-type-h.md#websocket_onmessagecallback) onMessage | Pointer to the callback invoked when the WebSocket client receives a message.<br><!--Device-WebSocket_OnMessageCallback onMessage--><!--Device-WebSocket_OnMessageCallback onMessage-End--> |
| [WebSocket_OnErrorCallback](capi-net-websocket-type-h.md#websocket_onerrorcallback) onError | Pointer to the callback invoked when the WebSocket client receives an error message.<br><!--Device-WebSocket_OnErrorCallback onError--><!--Device-WebSocket_OnErrorCallback onError-End--> |
| [WebSocket_OnCloseCallback](capi-net-websocket-type-h.md#websocket_onclosecallback) onClose | Pointer to the callback invoked when the WebSocket client receives a close message.<br><!--Device-WebSocket_OnCloseCallback onClose--><!--Device-WebSocket_OnCloseCallback onClose-End--> |
| [WebSocket_RequestOptions](capi-netstack-websocket-requestoptions.md) requestOptions | Options of the connection request.<br><!--Device-WebSocket_RequestOptions requestOptions--><!--Device-WebSocket_RequestOptions requestOptions-End--> |


