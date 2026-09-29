# net_websocket_type.h

## Overview

Defines the data structure for the C APIs of the WebSocket client module.

**Library**: libnet_websocket.so

**Since**: 11

**Related module**: [netstack](capi-netstack.md)

## Summary

### Struct

| Name | Description |
| -- | -- |
| [WebSocket_CloseResult](capi-netstack-websocket-closeresult.md) | Defines the parameters for the connection closure received by the WebSocket client. |
| [WebSocket_CloseOption](capi-netstack-websocket-closeoption.md) | Defines the parameters for the proactive connection closure initiated by the WebSocket client. |
| [WebSocket_ErrorResult](capi-netstack-websocket-errorresult.md) | Defines the parameters for the connection error received by the WebSocket client. |
| [WebSocket_OpenResult](capi-netstack-websocket-openresult.md) | Defines the parameters for the connection success received by the WebSocket client. |
| [WebSocket_Header](capi-netstack-websocket-header.md) | Defines the header linked list added to the WebSocket client. |
| [WebSocket_RequestOptions](capi-netstack-websocket-requestoptions.md) | Defines the parameters for the connection between the WebSocket client and server. |
| [WebSocket](capi-netstack-websocket.md) | Defines the parameters for the connection closure received by the WebSocket client. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [WebSocket_ErrCode](#websocket_errcode) | WebSocket_ErrCode | Defines the parameters for the connection closure received by the WebSocket client. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*WebSocket_OnOpenCallback)(struct WebSocket *client, WebSocket_OpenResult openResult)](#websocket_onopencallback) | WebSocket_OnOpenCallback | Callback invoked when the WebSocket client receives an **Open** message. |
| [typedef void (\*WebSocket_OnMessageCallback)(struct WebSocket *client, char *data, uint32_t length)](#websocket_onmessagecallback) | WebSocket_OnMessageCallback | Callback invoked when the WebSocket client receives a **Message** message. |
| [typedef void (\*WebSocket_OnErrorCallback)(struct WebSocket *client, WebSocket_ErrorResult errorResult)](#websocket_onerrorcallback) | WebSocket_OnErrorCallback | Callback invoked when the WebSocket client receives an **Error** message. |
| [typedef void (\*WebSocket_OnCloseCallback)(struct WebSocket *client, WebSocket_CloseResult closeResult)](#websocket_onclosecallback) | WebSocket_OnCloseCallback | Callback invoked when the WebSocket client receives a **Close** message. |

### Variable

| Name | Description |
| -- | -- |
| void (*WebSocket_OnOpenCallback)(struct WebSocket *client, WebSocket_OpenResult openResult) | Callback invoked when the WebSocket client receives an **Open** message.<br>**Since**: 11<br>**System capability**: SystemCapability.Communication.NetStack |
| void (*WebSocket_OnMessageCallback)(struct WebSocket *client, char *data, uint32_t length) | Callback invoked when the WebSocket client receives a **Message** message.<br>**Since**: 11<br>**System capability**: SystemCapability.Communication.NetStack |
| void (*WebSocket_OnErrorCallback)(struct WebSocket *client, WebSocket_ErrorResult errorResult) | Callback invoked when the WebSocket client receives an **Error** message.<br>**Since**: 11<br>**System capability**: SystemCapability.Communication.NetStack |
| void (*WebSocket_OnCloseCallback)(struct WebSocket *client, WebSocket_CloseResult closeResult) | Callback invoked when the WebSocket client receives a **Close** message.<br>**Since**: 11<br>**System capability**: SystemCapability.Communication.NetStack |

## Enum type description

### WebSocket_ErrCode

```c
enum WebSocket_ErrCode
```

**Description**

Defines the parameters for the connection closure received by the WebSocket client.

**Since**: 11

| Enum item | Description |
| -- | -- |
| WEBSOCKET_OK = 0 | Operation successful. |
| E_BASE = 1000 | Base value of the error code. |
| WEBSOCKET_CLIENT_NULL = (E_BASE + 1) | The WebSocket client is empty. |
| WEBSOCKET_CLIENT_NOT_CREATED = (E_BASE + 2) | The WebSocket client is not created. |
| WEBSOCKET_CONNECTION_ERROR = (E_BASE + 3) | An error occurred during WebSocket connection establishment. |
| WEBSOCKET_CONNECTION_PARSE_URL_ERROR = (E_BASE + 5) | An error occurred when parsing WebSocket connection parameters. |
| WEBSOCKET_CONNECTION_NO_MEMORY = (E_BASE + 6) | The memory is insufficient during WebSocket client connection establishment. |
| WEBSOCKET_CONNECTION_CLOSED_BY_PEER = (E_BASE + 7) | The WebSocket connection is closed by the peer end. |
| WEBSOCKET_DESTROYED = (E_BASE + 8) | The WebSocket connection is disconnected. |
| WEBSOCKET_PROTOCOL_ERROR = (E_BASE + 9) | Incorrect protocol. |
| WEBSOCKET_SEND_NO_MEMORY = (E_BASE + 10) | The system memory is insufficient when the WebSocket client sends data. |
| WEBSOCKET_SEND_DATA_NULL = (E_BASE + 11) | The sent data is empty. |
| WEBSOCKET_DATA_LENGTH_EXCEEDED = (E_BASE + 12) | The length of the sent data exceeds the limit. |
| WEBSOCKET_QUEUE_LENGTH_EXCEEDED = (E_BASE + 13) | The length of the sent data queue exceeds the limit. |
| WEBSOCKET_NO_CLIENT_CONTEXT = (E_BASE + 14) | The context of the WebSocket client is null. |
| WEBSOCKET_NO_HEADER_CONTEXT = (E_BASE + 15) | The protocol header of the WebSocket client is empty. |
| WEBSOCKET_HEADER_EXCEEDED = (E_BASE + 16) | The protocol header of the WebSocket client exceeds the limit. |
| WEBSOCKET_NO_CONNECTION = (E_BASE + 17) | The WebSocket client is not connected. |
| WEBSOCKET_NO_CONNECTION_CONTEXT = (E_BASE + 18) | No WebSocket connection context is released. |


## Function description

### WebSocket_OnOpenCallback()

```c
typedef void (*WebSocket_OnOpenCallback)(struct WebSocket *client, WebSocket_OpenResult openResult)
```

**Description**

Callback invoked when the WebSocket client receives an **Open** message.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [struct WebSocket](capi-netstack-websocket.md) *client | WebSocket client. |
| [WebSocket_OpenResult](capi-netstack-websocket-openresult.md) openResult | Content of the **Open** message sent from the WebSocket server to client. |

### WebSocket_OnMessageCallback()

```c
typedef void (*WebSocket_OnMessageCallback)(struct WebSocket *client, char *data, uint32_t length)
```

**Description**

Callback invoked when the WebSocket client receives a **Message** message.

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

Callback invoked when the WebSocket client receives an **Error** message.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [struct WebSocket](capi-netstack-websocket.md) *client | WebSocket client. |
| [WebSocket_ErrorResult](capi-netstack-websocket-errorresult.md) errorResult | Content of the **Error** message sent from the WebSocket server to client. |

### WebSocket_OnCloseCallback()

```c
typedef void (*WebSocket_OnCloseCallback)(struct WebSocket *client, WebSocket_CloseResult closeResult)
```

**Description**

Callback invoked when the WebSocket client receives a **Close** message.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [struct WebSocket](capi-netstack-websocket.md) *client | WebSocket client. |
| [WebSocket_CloseResult](capi-netstack-websocket-closeresult.md) closeResult | Content of the **Close** message sent from the WebSocket server to client. |


