# 使用WebSocket访问网络
<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

## 场景介绍

WebSocket是一种网络通信协议，它允许客户端和服务器之间建立一个持久的连接，并在该连接上进行全双工通信，连接之后客户端和服务器端可以同时主动发送数据，这是WebSocket和传统的HTTP协议最大的区别，HTTP以单向通信为主，客户端发起请求，服务器端响应数据，一次传输之后，连接会断开。一般情况下，HTTP适用于一次性数据获取（如网页内容加载），Websocket适用于实时性要求高的场景下（如在线聊天、实时游戏），以避免频繁建立连接提升用户体验。

该模块给第三方应用提供webSocket客户端和服务端能力，实现客户端与服务端的双向连接。

客户端：使用WebSocket建立服务器与客户端的双向连接，需要先通过[createWebSocket()](../reference/apis-network-kit/js-apis-webSocket.md#websocketcreatewebsocket)方法创建[WebSocket](../reference/apis-network-kit/js-apis-webSocket.md#websocket)对象，然后通过[connect()](../reference/apis-network-kit/js-apis-webSocket.md#connect)方法连接到服务器。当连接成功后，客户端会收到[open](../reference/apis-network-kit/js-apis-webSocket.md#onopen)事件的回调，之后客户端就可以通过[send()](../reference/apis-network-kit/js-apis-webSocket.md#send)方法与服务器进行通信。当服务器发信息给客户端时，客户端会收到[message](../reference/apis-network-kit/js-apis-webSocket.md#onmessage)事件的回调。当客户端想要取消此连接时，通过调用[close()](../reference/apis-network-kit/js-apis-webSocket.md#close)方法主动断开连接后，客户端会收到[close](../reference/apis-network-kit/js-apis-webSocket.md#onclose)事件的回调。若在上述任一过程中发生错误，客户端会收到[error](../reference/apis-network-kit/js-apis-webSocket.md#onerror)事件的回调。

服务端：（从API version 23开始支持全设备使用，之前仅支持TV设备使用）使用WebSocket建立服务器与客户端的双向连接，需要先通过[createWebSocketServer()](../reference/apis-network-kit/js-apis-webSocket.md#websocketcreatewebsocketserver19)方法创建[WebSocketServer](../reference/apis-network-kit/js-apis-webSocket.md#websocketserver19)对象，然后通过[start()](../reference/apis-network-kit/js-apis-webSocket.md#start19)方法启动服务器，监听客户端申请建链的消息。当连接成功后，服务端会收到[connect](../reference/apis-network-kit/js-apis-webSocket.md#onconnect19)事件的回调，之后服务端可以通过[send()](../reference/apis-network-kit/js-apis-webSocket.md#send19)方法与客户端进行通信，可以通过[listAllConnections()](../reference/apis-network-kit/js-apis-webSocket.md#listallconnections19)方法列举出当前与服务端建链的所有客户端信息。当客户端给服务端发消息时，服务端会收到[messageReceive](../reference/apis-network-kit/js-apis-webSocket.md#onmessagereceive19)事件回调。当服务端想断开某个与客户端的连接时，可以通过调用[close()](../reference/apis-network-kit/js-apis-webSocket.md#close19)方法主动断开与某个客户端的连接，之后服务端会收到[close](../reference/apis-network-kit/js-apis-webSocket.md#onclose19)事件的回调。当服务端想停止service时，可以调用[stop()](../reference/apis-network-kit/js-apis-webSocket.md#stop19)方法。若在上述任一过程中发生错误，服务端会收到[error](../reference/apis-network-kit/js-apis-webSocket.md#onerror19)事件的回调。

> **说明：**
>
> websocket支持[心跳检测机制](https://datatracker.ietf.org/doc/html/rfc6455#section-5.5.2)，在客户端和服务端建立webSocket连接之后，从连接建立或者客户端收到Pong帧开始计时，每间隔pingInterval秒客户端会发送Ping帧给服务器。服务器若支持websocket协议则会在收到Ping帧后自动回复Pong帧，表示连接正常，若服务端异常或服务端不支持websocket协议则不会回复Pong帧；若Ping帧发出去后，pongTimeout秒内没有收到Pong帧，则会主动断开连接。支持开发者关闭心跳检测机制，自定义pingInterval与pongTimeout，详情请参考[WebsocketRequestOptions](../reference/apis-network-kit/js-apis-webSocket.md#websocketrequestoptions)。
> 服务端从API version 19开始支持。

## client端开发步骤

1. 导入webSocket以及错误码模块。

   <!-- @[WebSocket_case_module_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/WebSocket_case/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   import { webSocket } from '@kit.NetworkKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { hilog } from '@kit.PerformanceAnalysisKit';
   ```
2. 创建WebSocket连接，返回一个WebSocket对象。

   <!-- @[WebSocket_creat_websocket](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/WebSocket_case/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   let defaultIpAddress = 'wss://echo.websocket.org'; // WebSocket地址
   let ws: webSocket.WebSocket = webSocket.createWebSocket();
   ```

3. 订阅WebSocket的打开、消息接收、关闭、Error事件（可选），当收到on('open')事件时，可以通过send()方法与服务器进行通信，当收到服务器的`bye`消息时（此消息字段仅为示意，具体字段需要与服务器协商），主动断开连接。

   <!-- @[websocket_open_message_close_error_methods](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/WebSocket_case/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   ws.on('open', (err: BusinessError, value: Object) => {
     hilog.info(0x0000, 'testTag', 'on open, status:' + JSON.stringify(value));
     // 当收到on('open')事件时，可以通过send()方法与服务器进行通信。
     // ...
   });
   
   ws.on('message', (err: BusinessError, value: string | ArrayBuffer) => {
     // ...
     hilog.info(0x0000, 'testTag', 'on message, message:' + value);
     // 当收到服务器的`bye`消息时（此消息字段仅为示意，具体字段需要与服务器协商），主动断开连接。
     if (value === 'bye') {
       ws!.close((err: BusinessError) => {
         if (!err) {
           // ...
           hilog.info(0x0000, 'testTag', `WebSocket closed successfully`);
         } else {
           // ...
           hilog.error(0x0000, 'testTag', `WebSocket closing failed: ` + JSON.stringify(err));
         }
       });
     }
   })
   
   ws.on('close', (err: BusinessError, value: webSocket.CloseResult) => {
    hilog.info(0x0000, 'testTag', 'on close, code is ' + value.code + ', reason is ' + value.reason);
     // ...
   });
   
   ws.on('error', (err: BusinessError) => {
     // ...
     hilog.error(0x0000, 'testTag', 'WebSocket error: ' + JSON.stringify(err));
   });
   ```

4. 根据URL地址，发起WebSocket连接。

   <!-- @[webSocket_case_object_connect](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/WebSocket_case/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   ws.connect(defaultIpAddress, (err: BusinessError, value: boolean) => {
     if (!err) {
       hilog.info(0x0000, 'testTag', 'Connected successfully');
     } else {
       // ...
       hilog.error(0x0000, 'testTag', `WebSocket connection failed: ` + JSON.stringify(err));
     }
   });
   ```

5. 收到on('open')的回调事件后，可通过send()方法向服务器发送数据。

   <!-- @[webSocket_case_send_message](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/WebSocket_case/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   ws.send('Hello, server!', (err: BusinessError, value: boolean) => {
     if (!err) {
       // ...
       hilog.info(0x0000, 'testTag', 'Message sent successfully');
     } else {
       // ...
       hilog.error(0x0000, 'testTag', `Message sending failed: ` + JSON.stringify(err));
     }
   });
   ```

## server端开发步骤

1. 导入webSocket以及错误码模块。

   <!-- @[WebSocket_server_case_module_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/WebSocket_Server_case/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   import { webSocket } from '@kit.NetworkKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { hilog } from '@kit.PerformanceAnalysisKit';
   ```

2. 创建WebSocketServer对象。

   <!-- @[WebSocket_server_creat_websocket](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/WebSocket_Server_case/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   let localServer: webSocket.WebSocketServer;
   localServer = webSocket.createWebSocketServer();
   ```

3. 订阅WebSocketServer的客户端连接事件、消息接收事件、关闭事件、Error事件（可选），在收到客户端连接事件后，服务端可以通过send()方法与客户端进行通信，当收到客户端的"bye"消息时（此消息字段仅为示意，具体字段需要与客户端协商），主动断开连接。

   <!-- @[websocket_server_open_message_close_error_methods](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/WebSocket_Server_case/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   localServer.on('connect', async (connection: webSocket.WebSocketConnection) => {
     hilog.info(0x0000, 'testTag', `New client connected! Client ip: ${connection.clientIP}, Client port: ${connection.clientPort}`);
     // 当收到on('connect')事件时，可以通过send()方法与客户端进行通信。
     localServer.send("Hello, I'm server!", connection).then((success: boolean) => {
       if (success) {
         hilog.info(0x0000, 'testTag', 'message send successfully');
       } else {
         hilog.error(0x0000, 'testTag', 'message send failed');
       }
     }).catch((error: BusinessError) => {
       hilog.error(0x0000, 'testTag', `message send failed, Code: ${error.code}, message: ${error.message}`);
     });
   });
   
   localServer.on('messageReceive', (message: webSocket.WebSocketMessage) => {
     try {
       hilog.info(0x0000, 'testTag', `on message received, client: ${message.clientConnection}, data: ${message.data}`);
       // 当收到客户端的"bye"消息时（此消息字段仅为示意，具体字段需要与客户端协商），主动断开连接。
       if (message.data === 'bye') {
         localServer.close(message.clientConnection).then((success: boolean) => {
           if (success) {
             hilog.info(0x0000, 'testTag', 'close client successfully');
           } else {
             hilog.error(0x0000, 'testTag', 'close client failed');
           }
         });
       }
     } catch (error) {
       hilog.error(0x0000, 'testTag', `on messageReceive failed. Code: ${error.code}, message: ${error.message}`);
     }
   });
   
   localServer.on('close', (clientConnection: webSocket.WebSocketConnection, closeReason: webSocket.CloseResult) => {
     hilog.info(0x0000, 'testTag', `client close, client: ${clientConnection}, closeReason: Code: ${closeReason.code}, reason: ${closeReason.reason}`);
   });
   
   localServer.on('error', (error: BusinessError) => {
     hilog.error(0x0000, 'testTag', `error. Code: ${error.code}, message: ${error.message}`);
   });
   ```

4. 配置config参数启动server端服务。

   <!-- @[websocket_server_config](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/WebSocket_Server_case/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   let config: webSocket.WebSocketServerConfig = {
     // 监听端口。
     serverPort: 8080,
     maxConcurrentClientsNumber: 10,
     maxConnectionsForOneClient: 10,
   }
   localServer.start(config).then((success: boolean) => {
     if (success) {
       hilog.info(0x0000, 'testTag', 'WebSocket server started successfully');
     } else {
       hilog.error(0x0000, 'testTag', 'Failed to start WebSocket server');
     }
   }).catch((error: BusinessError) => {
     hilog.error(0x0000, 'testTag', `Failed to start. Code: ${error.code}, message: ${error.message}`);
   });
   ```

5. 服务端监听所有客户端连接状态（可选）。

   <!-- @[WebSocket_server_connections](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/WebSocket_Server_case/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   let connections: webSocket.WebSocketConnection[] = [];
   
   // ...
     try {
       connections = await localServer.listAllConnections();
       if (connections.length === 0) {
         hilog.info(0x0000, 'testTag', 'client list is empty');
         // ...
       } else {
         hilog.info(0x0000, 'testTag', `client list cnt: ${connections.length}, client connections list is: ${connections}`);
       }
     } catch (error) {
       hilog.error(0x0000, 'testTag', `Failed to listAllConnections. Code: ${error.code}, message: ${error.message}`);
       // ...
     }
   ```

6. 需要关闭WebSocketServer端服务器时，可以通过stop()停止服务。

   <!-- @[WebSocket_server_stop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/WebSocket_Server_case/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   localServer.stop().then((success: boolean) => {
     if (success) {
       hilog.info(0x0000, 'testTag', 'server stop service successfully');
       // ...
     } else {
       hilog.error(0x0000, 'testTag', 'server stop service failed');
       // ...
     }
   });
   ```

## 相关实例

针对WebSocket连接的开发，有以下相关实例可供参考：

- [WebSocket（ArkTS）（API9）](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Connectivity/WebSocket)

- [WebSocket Client示例](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/WebSocket_case)
- [WebSocket Server示例](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/WebSocket_Server_case)
