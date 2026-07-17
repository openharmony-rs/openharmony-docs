# net_websocket_type.h

## 概述

定义WebSocket客户端模块的C接口需要的数据结构。

**库：** libnet_websocket.so

**系统能力：** SystemCapability.Communication.NetStack

**起始版本：** 11

**相关模块：** [netstack](capi-netstack.md)

## 汇总

### 结构体

| 名称 | 描述 |
| -- | -- |
| [WebSocket_CloseResult](capi-netstack-websocket-closeresult.md) | websocket客户端接收到服务端关闭的参数。 |
| [WebSocket_CloseOption](capi-netstack-websocket-closeoption.md) | websocket客户端主动关闭的参数。 |
| [WebSocket_ErrorResult](capi-netstack-websocket-errorresult.md) | websocket客户端来自服务端连接错误的参数。 |
| [WebSocket_OpenResult](capi-netstack-websocket-openresult.md) | websocket客户端来自服务端连接成功的参数。 |
| [WebSocket_Header](capi-netstack-websocket-header.md) | websocket客户端增加header的链表节点。 |
| [WebSocket_RequestOptions](capi-netstack-websocket-requestoptions.md) | webSocket客户端和服务端建立连接的参数。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*WebSocket_OnOpenCallback)(struct WebSocket *client, WebSocket_OpenResult openResult)](#websocket_onopencallback) | WebSocket_OnOpenCallback | websocket客户端接收open消息的回调函数定义。 |
| [typedef void (\*WebSocket_OnMessageCallback)(struct WebSocket *client, char *data, uint32_t length)](#websocket_onmessagecallback) | WebSocket_OnMessageCallback | websocket客户端接收数据的回调函数定义。 |
| [typedef void (\*WebSocket_OnErrorCallback)(struct WebSocket *client, WebSocket_ErrorResult errorResult)](#websocket_onerrorcallback) | WebSocket_OnErrorCallback | websocket客户端接收error错误消息的回调函数定义。 |
| [typedef void (\*WebSocket_OnCloseCallback)(struct WebSocket *client, WebSocket_CloseResult closeResult)](#websocket_onclosecallback) | WebSocket_OnCloseCallback | webSocket客户端接收close消息的回调函数定义。 |

### 变量

| 名称 | 描述 |
| -- | -- |
| [WebSocket_OnOpenCallback](capi-net-websocket-type-h.md#websocket_onopencallback) onOpen | Pointer to the callback invoked when the WebSocket client receives a connection message. |
| [WebSocket_OnMessageCallback](capi-net-websocket-type-h.md#websocket_onmessagecallback) onMessage | Pointer to the callback invoked when the WebSocket client receives a message. |
| [WebSocket_OnErrorCallback](capi-net-websocket-type-h.md#websocket_onerrorcallback) onError | Pointer to the callback invoked when the WebSocket client receives an error message. |
| [WebSocket_OnCloseCallback](capi-net-websocket-type-h.md#websocket_onclosecallback) onClose | Pointer to the callback invoked when the WebSocket client receives a close message. |
| [WebSocket_RequestOptions](capi-netstack-websocket-requestoptions.md) requestOptions | 客户端建立连接请求内容。 |

## 函数说明

### WebSocket_OnOpenCallback()

```c
typedef void (*WebSocket_OnOpenCallback)(struct WebSocket *client, WebSocket_OpenResult openResult)
```

**描述**

websocket客户端接收open消息的回调函数定义。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (struct WebSocket \*client | websocket客户端。 |
| [WebSocket_OpenResult](capi-netstack-websocket-openresult.md) openResult | websocket客户端接收建立连接消息的内容。 |

### WebSocket_OnMessageCallback()

```c
typedef void (*WebSocket_OnMessageCallback)(struct WebSocket *client, char *data, uint32_t length)
```

**描述**

websocket客户端接收数据的回调函数定义。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (struct WebSocket \*client | websocket客户端。 |
| char \*data | Data received by the websocket客户端。 |
| uint32_t length | Length of the data received by the websocket客户端。 |

### WebSocket_OnErrorCallback()

```c
typedef void (*WebSocket_OnErrorCallback)(struct WebSocket *client, WebSocket_ErrorResult errorResult)
```

**描述**

websocket客户端接收error错误消息的回调函数定义。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (struct WebSocket \*client | websocket客户端。 |
| [WebSocket_ErrorResult](capi-netstack-websocket-errorresult.md) errorResult | websocket客户端接收连接错误消息的内容。 |

### WebSocket_OnCloseCallback()

```c
typedef void (*WebSocket_OnCloseCallback)(struct WebSocket *client, WebSocket_CloseResult closeResult)
```

**描述**

webSocket客户端接收close消息的回调函数定义。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (struct WebSocket \*client | websocket客户端。 |
| [WebSocket_CloseResult](capi-netstack-websocket-closeresult.md) closeResult | webSocket客户端接收关闭消息的内容。 |


