# @ohos.net.webSocket(WebSocket连接)

给第三方应用提供webSocket客户端和服务端服务器，实现客户端与服务端的双向连接。客户端：使用WebSocket建立服务器与客户端的双向连接，需要先通过[createWebSocket](arkts-network-websocket-createwebsocket-f.md)方法创建 [WebSocket](arkts-network-websocket-websocket-i.md)对象，然后通过 [connect](arkts-network-websocket-websocket-i.md#connect)方法连接到服务器。当连接成功后，客户端会收到 open事件的回调，之后客户端就可以通过 [send](arkts-network-websocket-websocket-i.md#send)方法与服务器进行通信。当服务器发信 息给客户端时，客户端会收到message事 件的回调。当客户端想要取消此连接时，通过调用[close](arkts-network-websocket-websocket-i.md#close)方法主动断开连接后，客户端会收到 close事件的回调。若在上述任一过程中发生错误，客户端会收到 [error](arkts-network-websocket-websocket-i.md#onerror)事件的回调。服务端：（从API version 23开始支持全设备使用，之前仅支持TV设备使用）使用WebSocket建立服务器与客户端的双向连接，需要先通过 [createWebSocketServer](arkts-network-websocket-createwebsocketserver-f.md)方法创建[WebSocketServer](arkts-network-websocket-websocketserver-i.md)对 象，然后通过[start](arkts-network-websocket-websocketserver-i.md#start)方法启动服务器，监听客户端的申请建链的消息。当连接成功后，服务端会收到 connect事件的回调，之后服务端可以通 过[send](arkts-network-websocket-websocketserver-i.md#send)方法与客户端进行通信，或者通过 [listAllConnections](arkts-network-websocket-websocketserver-i.md#listallconnections)方法列举出当前与服务端建链的所有客户端信息。当客户端给服务端发消息时，服务端会收到 messageReceive事件回 调。当服务端想断开与某个客户端的连接时，可以通过调用[close](arkts-network-websocket-websocketserver-i.md#close)方法主动断开与某个客户端的连接，之后服务端会收到 [close](arkts-network-websocket-websocketserver-i.md#onclose)事件的回调。当服务端想停止 service时，可以调用[stop](arkts-network-websocket-websocketserver-i.md#stop)方法。若在上述任一过程中发生错误，服务端会收到 [error](arkts-network-websocket-websocketserver-i.md#onerror)事件的回调。

**起始版本：** 6

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createWebSocket(WebSocket连接)](arkts-network-websocket-createwebsocket-f.md) | 创建一个WebSocket对象，里面包括建立连接、关闭连接、发送数据和订阅/取消订阅WebSocket连接的打开事件、接收到服务器消息事件、关闭事件和错误事件。 |
| [createWebSocketServer(WebSocket连接)](arkts-network-websocket-createwebsocketserver-f.md) | 创建一个WebSocketServer对象，包括启动服务、发送数据、关闭连接、列出客户端信息、停止服务，订阅/取消订阅webSocket连接的连接事件、接收到客户端消息事件、关闭事件和错误事件。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ClientCert(WebSocket连接)](arkts-network-websocket-clientcert-i.md) | 客户端证书类型。 |
| [CloseResult(WebSocket连接)](arkts-network-websocket-closeresult-i.md) | 关闭WebSocket连接时，订阅close事件得到的关闭结果。 |
| [ServerCert(WebSocket连接)](arkts-network-websocket-servercert-i.md) | 指定服务端证书的信息，包括服务端证书文件路径和服务端证书的私钥文件路径。 |
| [WebSocket(WebSocket连接)](arkts-network-websocket-websocket-i.md) | 在调用WebSocket的方法前，需要先通过[webSocket.createWebSocket](arkts-network-websocket-createwebsocket-f.md)创建一个WebSocket。 |
| [WebSocketCloseOptions(WebSocket连接)](arkts-network-websocket-websocketcloseoptions-i.md) | 关闭WebSocket连接时，可选参数的类型和说明。 |
| [WebSocketConnection(WebSocket连接)](arkts-network-websocket-websocketconnection-i.md) | 客户端信息，包括客户端的ip地址和端口号port。 |
| [WebSocketMessage(WebSocket连接)](arkts-network-websocket-websocketmessage-i.md) | 从指定客户端接收到的消息，包括客户端的信息和数据。 |
| [WebSocketOpenInfo(WebSocket连接)](arkts-network-websocket-websocketopeninfo-i.md) | WebSocket连接成功后的详细信息。 |
| [WebSocketRequestOptions(WebSocket连接)](arkts-network-websocket-websocketrequestoptions-i.md) | 建立WebSocket连接时，可选参数的类型和说明。 |
| [WebSocketServer(WebSocket连接)](arkts-network-websocket-websocketserver-i.md) | 在调用WebSocketServer方法前，需要先通过[webSocket.createWebSocketServer](arkts-network-websocket-createwebsocketserver-f.md)创建一个 WebSocketServer。 |
| [WebSocketServerConfig(WebSocket连接)](arkts-network-websocket-websocketserverconfig-i.md) | 启动服务端的service时，需要输入的配置信息和说明。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [TlsProtocol(WebSocket连接)](arkts-network-websocket-tlsprotocol-e.md) | TLS协议类型。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ClientConnectionCloseCallback(WebSocket连接)](arkts-network-websocket-clientconnectionclosecallback-t.md) | 关闭WebSocketServer连接时，订阅close事件得到的指定客户端的关闭结果。 |
| [HttpProxy(WebSocket连接)](arkts-network-websocket-httpproxy-t.md) | 网络全局代理配置信息。 |
| [ProxyConfiguration(WebSocket连接)](arkts-network-websocket-proxyconfiguration-t.md) | 网络代理配置信息 |
| [ResponseHeaders(WebSocket连接)](arkts-network-websocket-responseheaders-t.md) | 服务器发送的响应头。 |
