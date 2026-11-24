# net_websocket_type.h

## Overview

Defines the data structure for the C APIs of the WebSocket client module.

**Library**: libnet_websocket.so

**System capability**: SystemCapability.Communication.NetStack

**Since**: 11

**Related module**: [netstack](capi-network-kit-netstack.md)

## Summary

### Structs

| Name | Description |
| -- | -- |
| [WebSocket_CloseResult](capi-netstack-websocket-closeresult.md) | Defines the parameters for the connection closure received by the WebSocket client. |
| [WebSocket_CloseOption](capi-netstack-websocket-closeoption.md) | Defines the parameters for the proactive connection closure initiated by the WebSocket client. |
| [WebSocket_ErrorResult](capi-netstack-websocket-errorresult.md) | Defines the parameters for the connection error received by the WebSocket client. |
| [WebSocket_OpenResult](capi-netstack-websocket-openresult.md) | Defines the parameters for the connection success received by the WebSocket client. |
| [WebSocket_Header](capi-netstack-websocket-header.md) | Defines the header linked list added to the WebSocket client. |
| [WebSocket_RequestOptions](capi-netstack-websocket-requestoptions.md) | Defines the parameters for the connection between the WebSocket client and server. |
| [WebSocket](capi-netstack-websocket.md) | Defines the struct of the WebSocket client. |

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [WebSocket_ErrCode](#websocket_errcode) | WebSocket_ErrCode | Defines the error codes of WebSocket requests. |

### Functions

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*WebSocket_OnOpenCallback)(struct WebSocket *client, WebSocket_OpenResult openResult)](#websocket_onopencallback) | WebSocket_OnOpenCallback | Defines a callback invoked when the WebSocket client receives an open message. |
| [typedef void (\*WebSocket_OnMessageCallback)(struct WebSocket *client, char *data, uint32_t length)](#websocket_onmessagecallback) | WebSocket_OnMessageCallback | Defines a callback invoked when the WebSocket client receives data. |
| [typedef void (\*WebSocket_OnErrorCallback)(struct WebSocket *client, WebSocket_ErrorResult errorResult)](#websocket_onerrorcallback) | WebSocket_OnErrorCallback | Defines a callback invoked when the WebSocket client receives an error message. |
| [typedef void (\*WebSocket_OnCloseCallback)(struct WebSocket *client, WebSocket_CloseResult closeResult)](#websocket_onclosecallback) | WebSocket_OnCloseCallback | Defines a callback invoked when the WebSocket client receives a close message. |

## Enum type description

### WebSocket_ErrCode

```c
enum WebSocket_ErrCode
```

**Description**

Defines the error codes of WebSocket requests.

<!--Device-enum WebSocket_ErrCode--><!--Device-enum WebSocket_ErrCode-End-->

**System capability**: SystemCapability.Communication.NetStack

**Since**: 11

| Enum item | Description |
| -- | -- |
| WEBSOCKET_OK = 0 | Operation successful.<br><!--Device-WEBSOCKET_OK = 0--><!--Device-WEBSOCKET_OK = 0-End--> |
| E_BASE = 1000 | Base value of the error code.<br><!--Device-E_BASE = 1000--><!--Device-E_BASE = 1000-End--> |
| WEBSOCKET_CLIENT_NULL = (E_BASE + 1) | The WebSocket client is empty.<br><!--Device-WEBSOCKET_CLIENT_NULL = (E_BASE + 1)--><!--Device-WEBSOCKET_CLIENT_NULL = (E_BASE + 1)-End--> |
| WEBSOCKET_CLIENT_NOT_CREATED = (E_BASE + 2) | The WebSocket client is not created.<br><!--Device-WEBSOCKET_CLIENT_NOT_CREATED = (E_BASE + 2)--><!--Device-WEBSOCKET_CLIENT_NOT_CREATED = (E_BASE + 2)-End--> |
| WEBSOCKET_CONNECTION_ERROR = (E_BASE + 3) | An error occurred during WebSocket connection establishment.<br><!--Device-WEBSOCKET_CONNECTION_ERROR = (E_BASE + 3)--><!--Device-WEBSOCKET_CONNECTION_ERROR = (E_BASE + 3)-End--> |
| WEBSOCKET_CONNECTION_PARSE_URL_ERROR = (E_BASE + 5) | An error occurred when parsing WebSocket connection parameters.<br><!--Device-WEBSOCKET_CONNECTION_PARSE_URL_ERROR = (E_BASE + 5)--><!--Device-WEBSOCKET_CONNECTION_PARSE_URL_ERROR = (E_BASE + 5)-End--> |
| WEBSOCKET_CONNECTION_NO_MEMORY = (E_BASE + 6) | The memory is insufficient during WebSocket client connection establishment.<br><!--Device-WEBSOCKET_CONNECTION_NO_MEMORY = (E_BASE + 6)--><!--Device-WEBSOCKET_CONNECTION_NO_MEMORY = (E_BASE + 6)-End--> |
| WEBSOCKET_CONNECTION_CLOSED_BY_PEER = (E_BASE + 7) | The WebSocket connection is closed by the peer end.<br><!--Device-WEBSOCKET_CONNECTION_CLOSED_BY_PEER = (E_BASE + 7)--><!--Device-WEBSOCKET_CONNECTION_CLOSED_BY_PEER = (E_BASE + 7)-End--> |
| WEBSOCKET_DESTROYED = (E_BASE + 8) | The WebSocket connection is disconnected.<br><!--Device-WEBSOCKET_DESTROYED = (E_BASE + 8)--><!--Device-WEBSOCKET_DESTROYED = (E_BASE + 8)-End--> |
| WEBSOCKET_PROTOCOL_ERROR = (E_BASE + 9) | Incorrect protocol.<br><!--Device-WEBSOCKET_PROTOCOL_ERROR = (E_BASE + 9)--><!--Device-WEBSOCKET_PROTOCOL_ERROR = (E_BASE + 9)-End--> |
| WEBSOCKET_SEND_NO_MEMORY = (E_BASE + 10) | The system memory is insufficient when the WebSocket client sends data.<br><!--Device-WEBSOCKET_SEND_NO_MEMORY = (E_BASE + 10)--><!--Device-WEBSOCKET_SEND_NO_MEMORY = (E_BASE + 10)-End--> |
| WEBSOCKET_SEND_DATA_NULL = (E_BASE + 11) | The sent data is empty.<br><!--Device-WEBSOCKET_SEND_DATA_NULL = (E_BASE + 11)--><!--Device-WEBSOCKET_SEND_DATA_NULL = (E_BASE + 11)-End--> |
| WEBSOCKET_DATA_LENGTH_EXCEEDED = (E_BASE + 12) | The length of the sent data exceeds the limit.<br><!--Device-WEBSOCKET_DATA_LENGTH_EXCEEDED = (E_BASE + 12)--><!--Device-WEBSOCKET_DATA_LENGTH_EXCEEDED = (E_BASE + 12)-End--> |
| WEBSOCKET_QUEUE_LENGTH_EXCEEDED = (E_BASE + 13) | The length of the sent data queue exceeds the limit.<br><!--Device-WEBSOCKET_QUEUE_LENGTH_EXCEEDED = (E_BASE + 13)--><!--Device-WEBSOCKET_QUEUE_LENGTH_EXCEEDED = (E_BASE + 13)-End--> |
| WEBSOCKET_NO_CLIENT_CONTEXT = (E_BASE + 14) | The context of the WebSocket client is null.<br><!--Device-WEBSOCKET_NO_CLIENT_CONTEXT = (E_BASE + 14)--><!--Device-WEBSOCKET_NO_CLIENT_CONTEXT = (E_BASE + 14)-End--> |
| WEBSOCKET_NO_HEADER_CONTEXT = (E_BASE + 15) | The protocol header of the WebSocket client is empty.<br><!--Device-WEBSOCKET_NO_HEADER_CONTEXT = (E_BASE + 15)--><!--Device-WEBSOCKET_NO_HEADER_CONTEXT = (E_BASE + 15)-End--> |
| WEBSOCKET_HEADER_EXCEEDED = (E_BASE + 16) | The protocol header of the WebSocket client exceeds the limit.<br><!--Device-WEBSOCKET_HEADER_EXCEEDED = (E_BASE + 16)--><!--Device-WEBSOCKET_HEADER_EXCEEDED = (E_BASE + 16)-End--> |
| WEBSOCKET_NO_CONNECTION = (E_BASE + 17) | The WebSocket client is not connected.<br><!--Device-WEBSOCKET_NO_CONNECTION = (E_BASE + 17)--><!--Device-WEBSOCKET_NO_CONNECTION = (E_BASE + 17)-End--> |
| WEBSOCKET_NO_CONNECTION_CONTEXT = (E_BASE + 18) | No WebSocket connection context is released.<br><!--Device-WEBSOCKET_NO_CONNECTION_CONTEXT = (E_BASE + 18)--><!--Device-WEBSOCKET_NO_CONNECTION_CONTEXT = (E_BASE + 18)-End--> |


## Function description

### WebSocket_OnOpenCallback()

```c
typedef void (*WebSocket_OnOpenCallback)(struct WebSocket *client, WebSocket_OpenResult openResult)
```

**Description**

Defines a callback invoked when the WebSocket client receives an open message.

<!--Device-typedef void (*WebSocket_OnOpenCallback)(struct WebSocket *client, WebSocket_OpenResult openResult)--><!--Device-typedef void (*WebSocket_OnOpenCallback)(struct WebSocket *client, WebSocket_OpenResult openResult)-End-->

**System capability**: SystemCapability.Communication.NetStack

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [struct WebSocket](capi-netstack-websocket.md) *client | Pointer to the WebSocket client. |
| [WebSocket_OpenResult](capi-netstack-websocket-openresult.md) openResult | Content of the connection establishment message received by the WebSocket client. |

### WebSocket_OnMessageCallback()

```c
typedef void (*WebSocket_OnMessageCallback)(struct WebSocket *client, char *data, uint32_t length)
```

**Description**

Defines a callback invoked when the WebSocket client receives data.

<!--Device-typedef void (*WebSocket_OnMessageCallback)(struct WebSocket *client, char *data, uint32_t length)--><!--Device-typedef void (*WebSocket_OnMessageCallback)(struct WebSocket *client, char *data, uint32_t length)-End-->

**System capability**: SystemCapability.Communication.NetStack

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [struct WebSocket](capi-netstack-websocket.md) *client | WebSocket client. |
| char *data | Data received by the WebSocket client. |
| uint32_t length | Length of the data received by the WebSocket client. |

### WebSocket_OnErrorCallback()

```c
typedef void (*WebSocket_OnErrorCallback)(struct WebSocket *client, WebSocket_ErrorResult errorResult)
```

**Description**

Defines a callback invoked when the WebSocket client receives an error message.

<!--Device-typedef void (*WebSocket_OnErrorCallback)(struct WebSocket *client, WebSocket_ErrorResult errorResult)--><!--Device-typedef void (*WebSocket_OnErrorCallback)(struct WebSocket *client, WebSocket_ErrorResult errorResult)-End-->

**System capability**: SystemCapability.Communication.NetStack

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [struct WebSocket](capi-netstack-websocket.md) *client | Pointer to the WebSocket client. |
| [WebSocket_ErrorResult](capi-netstack-websocket-errorresult.md) errorResult | Content of the connection error message received by the WebSocket client. |

### WebSocket_OnCloseCallback()

```c
typedef void (*WebSocket_OnCloseCallback)(struct WebSocket *client, WebSocket_CloseResult closeResult)
```

**Description**

Defines a callback invoked when the WebSocket client receives a close message.

<!--Device-typedef void (*WebSocket_OnCloseCallback)(struct WebSocket *client, WebSocket_CloseResult closeResult)--><!--Device-typedef void (*WebSocket_OnCloseCallback)(struct WebSocket *client, WebSocket_CloseResult closeResult)-End-->

**System capability**: SystemCapability.Communication.NetStack

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [struct WebSocket](capi-netstack-websocket.md) *client | WebSocket client. |
| [WebSocket_CloseResult](capi-netstack-websocket-closeresult.md) closeResult | Content of the close message received by the WebSocket client. |


