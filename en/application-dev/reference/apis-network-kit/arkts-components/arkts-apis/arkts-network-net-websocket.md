# @ohos.net.webSocket(WebSocket Connection)

Provides WebSocket clients and servers for third-party applications to implement bidirectional connections between the client and server.

On the WebSocket client: You can use WebSocket to establish a bidirectional connection between the server and client. Before doing this, you need to use the [createWebSocket](arkts-network-websocket-createwebsocket-f.md) API to create a [WebSocket](arkts-network-websocket-websocket-i.md) object and then use the [connect](arkts-network-websocket-websocket-i.md#connect) API to connect to the server. If the connection is successful, the client will receive a callback of the [open](arkts-network-websocket-websocket-i.md#onopen) event. Then, the client can communicate with the server using the [send](arkts-network-websocket-websocket-i.md#send) API. When the server sends a message to the client, the client will receive a callback of the [message](arkts-network-websocket-websocket-i.md#onmessage) event. If the connection is no longer needed, the client can call the [close](arkts-network-websocket-websocket-i.md#close) API to close the connection. After successful disconnection, the client will receive a callback of the [close](arkts-network-websocket-websocket-i.md#onclose) event. If an error occurs in any of the preceding processes, the client will receive a callback of the [error](arkts-network-websocket-websocket-i.md#onerror) event.

On the WebSocket server: Use the [createWebSocketServer](arkts-network-websocket-createwebsocketserver-f.md) method to create a [WebSocketServer](arkts-network-websocket-websocketserver-i.md) object, and then use the [start](arkts-network-websocket-websocketserver-i.md#start) method to start the server and listen to the link setup request message from the client. (The API version 23 and later versions support all devices. In earlier versions, only TV devices are supported.) If the connection is successful, the server receives the callback of the [connect](arkts-network-websocket-websocketserver-i.md#onconnect) event. The server can then communicate with the client by using the [send](arkts-network-websocket-websocketserver-i.md#send) API or obtain information about all connected clients by using the [listAllConnections](arkts-network-websocket-websocketserver-i.md#listallconnections) API. When the client sends a message to the server, the server receives the callback of the [messageReceive](arkts-network-websocket-websocketserver-i.md#onmessagereceive) event. If the connection is no longer needed, the server can call the [close](arkts-network-websocket-websocketserver-i.md#close) API to close the connection. After successful disconnection, the server will receive a callback of the [close](arkts-network-websocket-websocketserver-i.md#onclose) event. To stop the service, the server can use the [stop](arkts-network-websocket-websocketserver-i.md#stop) API. If an error occurs in any of the preceding processes, the server will receive a callback of the [error](arkts-network-websocket-websocketserver-i.md#onerror) event.

**Since:** 6

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { webSocket } from '@kit.NetworkKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createWebSocket](arkts-network-websocket-createwebsocket-f.md) | Creates a **WebSocket** object, which provides methods to create or close a WebSocket connection, send data over the connection, and enable or disable listening for the **open**, **close**, **message**, and **error** events. |
| [createWebSocketServer](arkts-network-websocket-createwebsocketserver-f.md) | Creates a **WebSocketServer** object, which provides methods to start or stop the WebSocketServer service, send data over the connection, close the connection, list all connections, and enable or disable listening for the **open**, **close**, **message**, and **error** events. |

### Interfaces

| Name | Description |
| --- | --- |
| [ClientCert](arkts-network-websocket-clientcert-i.md) | Defines the client certificate type. |
| [CloseResult](arkts-network-websocket-closeresult-i.md) | Represents the result obtained from the **close** event reported when the WebSocket connection is closed. |
| [ServerCert](arkts-network-websocket-servercert-i.md) | Certificate information, which includes the paths of the WebSocketServer certificate file and private key file. |
| [WebSocket](arkts-network-websocket-websocket-i.md) | Defines a **WebSocket** object. Before invoking WebSocket APIs, you need to call [webSocket.createWebSocket](arkts-network-websocket-createwebsocket-f.md) to create a **WebSocket** object. |
| [WebSocketCloseOptions](arkts-network-websocket-websocketcloseoptions-i.md) | Defines the optional parameters carried in the request for closing a WebSocket connection. |
| [WebSocketConnection](arkts-network-websocket-websocketconnection-i.md) | Client information, including the IP address and port number. |
| [WebSocketMessage](arkts-network-websocket-websocketmessage-i.md) | Callback used to return the result, which contains: |
| [WebSocketOpenInfo](arkts-network-websocket-websocketopeninfo-i.md) | The result for open info of a WebSocket connection. |
| [WebSocketRequestOptions](arkts-network-websocket-websocketrequestoptions-i.md) | Defines the optional parameters carried in the request for establishing a WebSocket connection. |
| [WebSocketServer](arkts-network-websocket-websocketserver-i.md) | Defines a **WebSocketServer** object. You need to use [webSocket.createWebSocketServer](arkts-network-websocket-createwebsocketserver-f.md) to create a **WebSocketServer** object before using its methods. |
| [WebSocketServerConfig](arkts-network-websocket-websocketserverconfig-i.md) | Defines the WebSocketServer configuration. |

### Enums

| Name | Description |
| --- | --- |
| [TlsProtocol](arkts-network-websocket-tlsprotocol-e.md) | Enumerates the TLS protocol types. |

### Types

| Name | Description |
| --- | --- |
| [ClientConnectionCloseCallback](arkts-network-websocket-clientconnectionclosecallback-t.md) | Callback invoked when the WebSocketServer connection is closed. |
| [HttpProxy](arkts-network-websocket-httpproxy-t.md) | Defines the global HTTP proxy configuration of the network. |
| [ProxyConfiguration](arkts-network-websocket-proxyconfiguration-t.md) | Represents the HTTP proxy configuration. |
| [ResponseHeaders](arkts-network-websocket-responseheaders-t.md) | Enumerates the response headers sent by the server. |
