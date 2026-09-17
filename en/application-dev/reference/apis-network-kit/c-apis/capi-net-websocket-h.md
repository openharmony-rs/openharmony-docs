# net_websocket.h

## Overview

Defines the APIs for the websocket client module.

**Library**: libnet_websocket.so

**System capability**: SystemCapability.Communication.NetStack

**Since**: 11

**Related module**: [netstack](capi-netstack.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [struct WebSocket *OH_WebSocketClient_Constructor(WebSocket_OnOpenCallback onOpen, WebSocket_OnMessageCallback onMessage, WebSocket_OnErrorCallback onError, WebSocket_OnCloseCallback onclose)](#oh_websocketclient_constructor) | Constructor used to create a WebSocket client. |
| [int OH_WebSocketClient_AddHeader(struct WebSocket *client, struct WebSocket_Header header)](#oh_websocketclient_addheader) | Adds the header information to the client request. |
| [int OH_WebSocketClient_Connect(struct WebSocket *client, const char *url, struct WebSocket_RequestOptions options)](#oh_websocketclient_connect) | Connects the WebSocket client to the server. |
| [int OH_WebSocketClient_Send(struct WebSocket *client, char *data, size_t length)](#oh_websocketclient_send) | Sends data from the WebSocket client to the server. |
| [int OH_WebSocketClient_Close(struct WebSocket *client, struct WebSocket_CloseOption options)](#oh_websocketclient_close) | Closes the connection on the WebSocket client. |
| [int OH_WebSocketClient_Destroy(struct WebSocket *client)](#oh_websocketclient_destroy) | Destroys the WebSocket client and releases the context and resources of the WebSocket connection. Usage: |

## Function description

### OH_WebSocketClient_Constructor()

```c
struct WebSocket *OH_WebSocketClient_Constructor(WebSocket_OnOpenCallback onOpen, WebSocket_OnMessageCallback onMessage, WebSocket_OnErrorCallback onError, WebSocket_OnCloseCallback onclose)
```

**Description**

Constructor used to create a WebSocket client.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| WebSocket_OnOpenCallback onOpen | Callback invoked when the WebSocket client receives an **open** message. |
| WebSocket_OnMessageCallback onMessage | Callback invoked when the WebSocket client receives a **Message** message. |
| WebSocket_OnErrorCallback onError | Callback invoked when the WebSocket client receives an **error** message. |
| WebSocket_OnCloseCallback onclose | Callback invoked when the WebSocket client receives a **close** message. |

**Returns**:

| Type | Description |
| -- | -- |
| struct WebSocket * | Pointer to the WebSocket client if the operation is successful; NULL otherwise. |

### OH_WebSocketClient_AddHeader()

```c
int OH_WebSocketClient_AddHeader(struct WebSocket *client, struct WebSocket_Header header)
```

**Description**

Adds the header information to the client request.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct WebSocket *client | Pointer to the WebSocket client. |
| struct WebSocket_Header header | Header information. |

**Returns**:

| Type | Description |
| -- | -- |
| int | 0 if the operation is successful; a non-0 value otherwise. For details about the return values, see       OH_Websocket_ErrCode. |

### OH_WebSocketClient_Connect()

```c
int OH_WebSocketClient_Connect(struct WebSocket *client, const char *url, struct WebSocket_RequestOptions options)
```

**Description**

Connects the WebSocket client to the server.

**System capability**: SystemCapability.Communication.NetStack

**Required permission**: ohos.permission.INTERNET

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct WebSocket *client | Pointer to the WebSocket client. |
| const char *url | IP address for the WebSocket client to connect to the server. |
| struct WebSocket_RequestOptions options | Optional parameters for connection establishment. |

**Returns**:

| Type | Description |
| -- | -- |
| int | 0 if the operation is successful; a non-0 value otherwise. For details about the return values, see       OH_Websocket_ErrCode. |

### OH_WebSocketClient_Send()

```c
int OH_WebSocketClient_Send(struct WebSocket *client, char *data, size_t length)
```

**Description**

Sends data from the WebSocket client to the server.

**System capability**: SystemCapability.Communication.NetStack

**Required permission**: ohos.permission.INTERNET

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct WebSocket *client | WebSocket client. |
| char *data | Data sent by the WebSocket client. |
| size_t length | Length of the data sent by the WebSocket client. |

**Returns**:

| Type | Description |
| -- | -- |
| int | 0 if the operation is successful; a non-0 value otherwise. For details about the return values, see       OH_Websocket_ErrCode. |

### OH_WebSocketClient_Close()

```c
int OH_WebSocketClient_Close(struct WebSocket *client, struct WebSocket_CloseOption options)
```

**Description**

Closes the connection on the WebSocket client.

**System capability**: SystemCapability.Communication.NetStack

**Required permission**: ohos.permission.INTERNET

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct WebSocket *client | WebSocket client. |
| struct WebSocket_CloseOption options | Optional parameters for connection closure. |

**Returns**:

| Type | Description |
| -- | -- |
| int | 0 if the operation is successful; a non-0 value otherwise. For details about the return values, see       OH_Websocket_ErrCode. |

### OH_WebSocketClient_Destroy()

```c
int OH_WebSocketClient_Destroy(struct WebSocket *client)
```

**Description**

Destroys the WebSocket client and releases the context and resources of the WebSocket connection. Usage:

**System capability**: SystemCapability.Communication.NetStack

**Required permission**: ohos.permission.INTERNET

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct WebSocket *client | WebSocket client. |

**Returns**:

| Type | Description |
| -- | -- |
| int | 0 if the operation is successful; a non-0 value otherwise. For details about the return values, see       OH_Websocket_ErrCode. |


