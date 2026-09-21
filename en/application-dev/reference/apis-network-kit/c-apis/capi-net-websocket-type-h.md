# net_websocket_type.h

## Overview

Defines the data structure for the C APIs of the WebSocket client module.

**Library**: libnet_websocket.so

**System capability**: SystemCapability.Communication.NetStack

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
| void (*WebSocket_OnOpenCallback)(struct WebSocket *client, WebSocket_OpenResult openResult) | Callback invoked when the WebSocket client receives an **Open** message.<br>**Since**: 11 |
| void (*WebSocket_OnMessageCallback)(struct WebSocket *client, char *data, uint32_t length) | Callback invoked when the WebSocket client receives a **Message** message.<br>**Since**: 11 |
| void (*WebSocket_OnErrorCallback)(struct WebSocket *client, WebSocket_ErrorResult errorResult) | Callback invoked when the WebSocket client receives an **Error** message.<br>**Since**: 11 |
| void (*WebSocket_OnCloseCallback)(struct WebSocket *client, WebSocket_CloseResult closeResult) | Callback invoked when the WebSocket client receives a **Close** message.<br>**Since**: 11 |

## Function description

### WebSocket_OnOpenCallback()

```c
typedef void (*WebSocket_OnOpenCallback)(struct WebSocket *client, WebSocket_OpenResult openResult)
```

**Description**

Callback invoked when the WebSocket client receives an **Open** message.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [struct WebSocket](capi-netstack-websocket.md) \*client | WebSocket client. |
| [WebSocket_OpenResult](capi-netstack-websocket-openresult.md) openResult | Content of the **Open** message sent from the WebSocket server to client. |

### WebSocket_OnMessageCallback()

```c
typedef void (*WebSocket_OnMessageCallback)(struct WebSocket *client, char *data, uint32_t length)
```

**Description**

Callback invoked when the WebSocket client receives a **Message** message.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [struct WebSocket](capi-netstack-websocket.md) \*client | WebSocket client. |
| char \*data | Data received by the WebSocket client. |
| uint32_t length | Length of the data received by the WebSocket client. |

### WebSocket_OnErrorCallback()

```c
typedef void (*WebSocket_OnErrorCallback)(struct WebSocket *client, WebSocket_ErrorResult errorResult)
```

**Description**

Callback invoked when the WebSocket client receives an **Error** message.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [struct WebSocket](capi-netstack-websocket.md) \*client | WebSocket client. |
| [WebSocket_ErrorResult](capi-netstack-websocket-errorresult.md) errorResult | Content of the **Error** message sent from the WebSocket server to client. |

### WebSocket_OnCloseCallback()

```c
typedef void (*WebSocket_OnCloseCallback)(struct WebSocket *client, WebSocket_CloseResult closeResult)
```

**Description**

Callback invoked when the WebSocket client receives a **Close** message.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [struct WebSocket](capi-netstack-websocket.md) \*client | WebSocket client. |
| [WebSocket_CloseResult](capi-netstack-websocket-closeresult.md) closeResult | Content of the **Close** message sent from the WebSocket server to client. |


