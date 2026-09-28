# net_websocket_type.h

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=c33290f86c4a896f90eff1ee86d78748f13424d1 translatedAt=2026-09-23T01:27:20.200Z pushedAt=2026-09-24T06:00:14.111Z -->

## Overview

Defines the data structures required by the C APIs of the WebSocket client module.

**File to include**: <network/netstack/net_websocket_type.h>

**Library**: libnet_websocket.so

**System capability**: SystemCapability.Communication.NetStack

**Since**: 11

**Related module**: [netstack](capi-netstack.md)

## Summary

### Structs

| Name| Description|
| -- | -- |
| [WebSocket_CloseResult](capi-netstack-websocket-closeresult.md) | Defines the parameters of the WebSocket client for closing from the server. |
| [WebSocket_CloseOption](capi-netstack-websocket-closeoption.md) | Defines the parameters of the WebSocket client for active closing. |
| [WebSocket_ErrorResult](capi-netstack-websocket-errorresult.md) | Defines the parameters of the WebSocket client for a connection error from the server. |
| [WebSocket_OpenResult](capi-netstack-websocket-openresult.md) | Defines the parameters of the WebSocket client for a successful connection from the server. |
| [WebSocket_Header](capi-netstack-websocket-header.md) | Defines the linked list node for adding a header to the WebSocket client. |
| [WebSocket_RequestOptions](capi-netstack-websocket-requestoptions.md) | Defines the parameters for establishing a connection between the WebSocket client and server. |
| [WebSocket](capi-netstack-websocket.md) | Defines the struct of the WebSocket client. |

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [typedef void (\*WebSocket_OnOpenCallback)(struct WebSocket *client, WebSocket_OpenResult openResult)](#websocket_onopencallback) | WebSocket_OnOpenCallback | Callback invoked when the WebSocket client receives an **Open** message.|
| [typedef void (\*WebSocket_OnMessageCallback)(struct WebSocket *client, char *data, uint32_t length)](#websocket_onmessagecallback) | WebSocket_OnMessageCallback | Callback invoked when the WebSocket client receives data.|
| [typedef void (\*WebSocket_OnErrorCallback)(struct WebSocket *client, WebSocket_ErrorResult errorResult)](#websocket_onerrorcallback) | WebSocket_OnErrorCallback | Callback invoked when the WebSocket client receives an **Error** message.|
| [typedef void (\*WebSocket_OnCloseCallback)(struct WebSocket *client, WebSocket_CloseResult closeResult)](#websocket_onclosecallback) | WebSocket_OnCloseCallback |Callback invoked when the WebSocket client receives a close message. |

## Enum Description

### WebSocket_ErrCode

```c
enum WebSocket_ErrCode
```

**Description**

Defines the error codes of WebSocket requests.

**Since**: 11

| Value| Description|
| -- | -- |
| WEBSOCKET_OK = 0 | Operation successful.|
| E_BASE = 1000 | Base value of the error code.|
| WEBSOCKET_CLIENT_NULL = (E_BASE + 1) | The WebSocket client is null. |
| WEBSOCKET_CLIENT_NOT_CREATED = (E_BASE + 2) | The WebSocket client is not created. |
| WEBSOCKET_CONNECTION_ERROR = (E_BASE + 3) | An error occurs when establishing the WebSocket connection. |
| WEBSOCKET_CONNECTION_PARSE_URL_ERROR = (E_BASE + 5) | An error occurs when parsing the WebSocket connection parameters. |
| WEBSOCKET_CONNECTION_NO_MEMORY = (E_BASE + 6) | Insufficient memory when the WebSocket client establishes a connection. |
| WEBSOCKET_CONNECTION_CLOSED_BY_PEER = (E_BASE + 7) | The WebSocket connection is closed by the peer. |
| WEBSOCKET_DESTROYED = (E_BASE + 8) | The WebSocket connection is disconnected. |
| WEBSOCKET_PROTOCOL_ERROR = (E_BASE + 9) | Incorrect protocol.|
| WEBSOCKET_SEND_NO_MEMORY = (E_BASE + 10) | Insufficient system memory when the WebSocket client sends data. |
| WEBSOCKET_SEND_DATA_NULL = (E_BASE + 11) | The sent data is empty.|
| WEBSOCKET_DATA_LENGTH_EXCEEDED = (E_BASE + 12) | The length of the sent data exceeds the limit.|
| WEBSOCKET_QUEUE_LENGTH_EXCEEDED = (E_BASE + 13) | The length of the sent data queue exceeds the limit.|
| WEBSOCKET_NO_CLIENT_CONTEXT = (E_BASE + 14) | The context of the WebSocket client is null. |
| WEBSOCKET_NO_HEADER_CONTEXT = (E_BASE + 15) | The protocol header of the WebSocket client is null. |
| WEBSOCKET_HEADER_EXCEEDED = (E_BASE + 16) | The protocol header of the WebSocket client exceeds the limit. |
| WEBSOCKET_NO_CONNECTION = (E_BASE + 17) | The WebSocket client is not connected. |
| WEBSOCKET_NO_CONNECTION_CONTEXT = (E_BASE + 18) | No corresponding context exists when releasing the WebSocket connection context. |

## Function Description

### WebSocket_OnOpenCallback()

```c
typedef void (*WebSocket_OnOpenCallback)(struct WebSocket *client, WebSocket_OpenResult openResult)
```

**Description**

Defines a callback invoked when the WebSocket client receives an open message.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [struct WebSocket](capi-netstack-websocket.md) *client | Pointer to the WebSocket client. |
| [WebSocket_OpenResult](capi-netstack-websocket-openresult.md) openResult | Content of the connection establishment message received by the WebSocket client. |

### WebSocket_OnMessageCallback()

```c
typedef void (*WebSocket_OnMessageCallback)(struct WebSocket *client, char *data, uint32_t length)
```

**Description**

Defines a callback invoked when the WebSocket client receives data.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [struct WebSocket](capi-netstack-websocket.md) *client | WebSocket client. |
|  char *data |   Data received by the WebSocket client. |
|  uint32_t length | Length of the data received by the WebSocket client. |

### WebSocket_OnErrorCallback()

```c
typedef void (*WebSocket_OnErrorCallback)(struct WebSocket *client, WebSocket_ErrorResult errorResult)
```

**Description**

Defines a callback invoked when the WebSocket client receives an error message.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [struct WebSocket](capi-netstack-websocket.md) *client | Pointer to the WebSocket client. |
| [WebSocket_ErrorResult](capi-netstack-websocket-errorresult.md) errorResult | Content of the connection error message received by the WebSocket client. |

### WebSocket_OnCloseCallback()

```c
typedef void (*WebSocket_OnCloseCallback)(struct WebSocket *client, WebSocket_CloseResult closeResult)
```

**Description**

Defines a callback invoked when the WebSocket client receives a close message.

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [struct WebSocket](capi-netstack-websocket.md) *client | WebSocket client. |
| [WebSocket_CloseResult](capi-netstack-websocket-closeresult.md) closeResult | Content of the close message received by the WebSocket client. |

