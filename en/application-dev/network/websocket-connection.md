# Using WebSocket for Network Access
<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

## When to Use

WebSocket is a network communication protocol that enables the establishment of a persistent connection between a client and a server, while facilitating full-duplex communication over this connection. Once the connection is established, both the client and the server can actively send data simultaneously. This constitutes the most significant difference between WebSocket and the traditional HTTP protocol. Unlike WebSocket, HTTP primarily relies on one-way (unidirectional) communication: a client initiates a request, the server side responds with data, and the connection is terminated once a single transfer is complete. Generally, HTTP is applicable to one-off data retrieval (such as web content loading). In contrast, WebSocket is ideal for scenarios with high real-time requirements (such as online chat and real-time games), preventing frequent connection establishment from affecting user experience.

The **webSocket** module implements bidirectional connections between the WebSocket client and WebSocket server for third-party applications. Currently, the WebSocket server is available only for smart TVs.

On the WebSocket client: Use WebSocket to establish a bidirectional connection between the server and the client. Before doing this, you need to use [createWebSocket()](../reference/apis-network-kit/js-apis-webSocket.md#websocketcreatewebsocket) to create a [WebSocket](../reference/apis-network-kit/js-apis-webSocket.md#websocket) object and then use [connect()](../reference/apis-network-kit/js-apis-webSocket.md#connect) to connect to the server. If the connection is successful, the client will receive a callback of the [open](../reference/apis-network-kit/js-apis-webSocket.md#onopen) event. Then, the client can communicate with the server by using [send()](../reference/apis-network-kit/js-apis-webSocket.md#send). When the server sends a message to the client, the client will receive a callback of the [message](../reference/apis-network-kit/js-apis-webSocket.md#onmessage) event. If the connection is no longer needed, the client can call [close()](../reference/apis-network-kit/js-apis-webSocket.md#close) to close the connection. After successful disconnection, the client will receive a callback of the [close](../reference/apis-network-kit/js-apis-webSocket.md#onclose) event. If an error occurs in any of the preceding processes, the client will receive a callback of the [error](../reference/apis-network-kit/js-apis-webSocket.md#onerror) event.

On the WebSocket server (available only for smart TVs): Use WebSocket to establish a bidirectional connection between the server and client. Before doing this, you need to use [createWebSocketServer()](../reference/apis-network-kit/js-apis-webSocket.md#websocketcreatewebsocketserver19) to create a [WebSocketServer](../reference/apis-network-kit/js-apis-webSocket.md#websocketserver19) object and then use [start()](../reference/apis-network-kit/js-apis-webSocket.md#start19) to start the server to listen for connection requests from the client. If the connection is successful, the server receives the callback of the [connect](../reference/apis-network-kit/js-apis-webSocket.md#onconnect19) event. The server can then communicate with the client by using [send()](../reference/apis-network-kit/js-apis-webSocket.md#send19) or obtain information about all connected clients by using [listAllConnections()](../reference/apis-network-kit/js-apis-webSocket.md#listallconnections19). When the client sends a message to the server, the server receives the callback of the [messageReceive](../reference/apis-network-kit/js-apis-webSocket.md#onmessagereceive19) event. If the connection is no longer needed, the server can call [close()](../reference/apis-network-kit/js-apis-webSocket.md#close19) to close the connection. After successful disconnection, the server will receive a callback of the [close](../reference/apis-network-kit/js-apis-webSocket.md#onclose19) event. To stop the service, the server can use the [stop()](../reference/apis-network-kit/js-apis-webSocket.md#stop19) API. If an error occurs in any of the preceding processes, the server will receive a callback of the [error](../reference/apis-network-kit/js-apis-webSocket.md#onerror19) event.

> **NOTE**
>
> The WebSocket module supports the [heartbeat detection mechanism](https://datatracker.ietf.org/doc/html/rfc6455#section-5.5.2). After a WebSocket connection is established between the client and server or before the client receives a Pong frame from the server, the client sends a Ping frame to the server at an interval specified by **pingInterval**. If the WebSocket server supports the WebSocket protocol, it automatically replies with a Pong frame after receiving a Ping frame, indicating that the connection is normal. If the server is abnormal or does not support the WebSocket protocol, the server does not reply with a Pong frame. If no Pong frame is received within the duration specified by **pongTimeout**, the connection is disconnected. You can enable the heartbeat detection mechanism and customize **pingInterval** and **pongTimeout** on demand. For details, see [WebsocketRequestOptions](../reference/apis-network-kit/js-apis-webSocket.md#websocketrequestoptions).
> The WebSocket server is supported since API version 19.

## Client Development Procedure

1. Import the **webSocket** and **BusinessError** modules.

<!-- @[WebSocket_case_module_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/WebSocket_case/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
```
2. Create a WebSocket connection. A **WebSocket** object is returned.

<!-- @[WebSocket_creat_websocket](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/WebSocket_case/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
let defaultIpAddress = 'wss://echo.websocket.org'; // WebSocket address
let ws: webSocket.WebSocket = webSocket.createWebSocket();
```

3. (Optional) Subscribe to the **open**, **message**, **close**, and **error** events of the **WebSocket** object. When receiving the on('open') event, the client can use the send() API to communicate with the server. When receiving the `bye` message (the actual message name may differ) from the server, the client proactively disconnects from the server.

<!-- @[websocket_open_message_close_error_methods](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/WebSocket_case/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
ws.on('open', (err: BusinessError, value: Object) => {
  hilog.info(0x0000, 'testTag', 'on open, status:' + JSON.stringify(value));
  // When receiving the on('open') event, the client can use the send() API to communicate with the server.
// ···
});

ws.on('message', (err: BusinessError, value: string | ArrayBuffer) => {
// ···
  hilog.info(0x0000, 'testTag', 'on message, message:' + value);
  // When receiving the `bye` message (the actual message name may differ) from the server, the client proactively disconnects from the server.
  if (value === 'bye') {
    ws!.close((err: BusinessError) => {
      if (!err) {
        // ···
        hilog.info(0x0000, 'testTag', `WebSocket closed successfully`);
      } else {
        // ···
        hilog.error(0x0000, 'testTag', `WebSocket closing failed: ` + JSON.stringify(err));
      }
    });
  }
})

ws.on('close', (err: BusinessError, value: webSocket.CloseResult) => {
 hilog.info(0x0000, 'testTag', 'on close, code is ' + value.code + ', reason is ' + value.reason);
// ···
});

ws.on('error', (err: BusinessError) => {
// ···
  hilog.error(0x0000, 'testTag', 'WebSocket error: ' + JSON.stringify(err));
});
```

4. Establish a WebSocket connection to a given URL.

<!-- @[webSocket_case_object_connect](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/WebSocket_case/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
ws.connect(defaultIpAddress, (err: BusinessError, value: boolean) => {
  if (!err) {
    hilog.info(0x0000, 'testTag', 'Connected successfully');
  } else {
    // ···
    hilog.error(0x0000, 'testTag', `WebSocket connection failed: ` + JSON.stringify(err));
  }
});
```

5. After receiving the **on('open')** callback event, use the **send()** method to send data to the server.

<!-- @[webSocket_case_send_message](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/WebSocket_case/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
ws.send('Hello, server!', (err: BusinessError, value: boolean) => {
  if (!err) {
    // ···
    hilog.info(0x0000, 'testTag', 'Message sent successfully');
  } else {
    // ···
    hilog.error(0x0000, 'testTag', `Message sending failed: ` + JSON.stringify(err));
  }
});
```

## Server Development Procedure

1. Import the **webSocket** and **BusinessError** modules.

    <!-- @[WebSocket_server_case_module_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/WebSocket_Server_case/entry/src/main/ets/pages/Index.ets) -->
        
    ``` TypeScript
    import { webSocket } from '@kit.NetworkKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    import { hilog } from '@kit.PerformanceAnalysisKit';
    ```

2. Create a **WebSocketServer** object.

    <!-- @[WebSocket_server_creat_websocket](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/WebSocket_Server_case/entry/src/main/ets/pages/Index.ets) -->
        
    ``` TypeScript
    let localServer: webSocket.WebSocketServer;
    localServer = webSocket.createWebSocketServer();
    ```

3. Subscribe to the **connect**, **message**, **close**, and **error** (optional) events of the **WebSocketServer** object. When receiving the on('connect') event, the server can use the **send()** API to communicate with the client. When receiving the `bye` message (the actual message name may differ) from the client, the server proactively disconnects from the client.

    <!-- @[websocket_server_open_message_close_error_methods](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/WebSocket_Server_case/entry/src/main/ets/pages/Index.ets) -->
      
    ``` TypeScript
    localServer.on('connect', async (connection: webSocket.WebSocketConnection) => {
      hilog.info(0x0000, 'testTag', `New client connected! Client ip: ${connection.clientIP}, Client port: ${connection.clientPort}`);
      // Use send() to send data to the client when the on('connect') event is received.
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
        // When receiving the bye message (the actual message name may differ) from the client, the server proactively disconnects from the client.
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

4. Configure **config** parameters for starting the WebSocket server.

    <!-- @[websocket_server_config](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/WebSocket_Server_case/entry/src/main/ets/pages/Index.ets) -->
        
    ``` TypeScript
    let config: webSocket.WebSocketServerConfig = {
      // Configure the listening port.
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

5. (Optional) Enable listening for the connection status of all clients.

    <!-- @[WebSocket_server_connections](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/WebSocket_Server_case/entry/src/main/ets/pages/Index.ets) -->
        
    ``` TypeScript
    let connections: webSocket.WebSocketConnection[] = [];
    
    // ···
      try {
        connections = await localServer.listAllConnections();
        if (connections.length === 0) {
          hilog.info(0x0000, 'testTag', 'client list is empty');
        // ···
        } else {
          hilog.info(0x0000, 'testTag', `client list cnt: ${connections.length}, client connections list is: ${connections}`);
        }
      } catch (error) {
        hilog.error(0x0000, 'testTag', `Failed to listAllConnections. Code: ${error.code}, message: ${error.message}`);
        // ···
      }
    ```

6. Call **stop()** to stop the WebSocket server if it is no longer needed.

    <!-- @[WebSocket_server_stop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/WebSocket_Server_case/entry/src/main/ets/pages/Index.ets) -->
        
    ``` TypeScript
    localServer.stop().then((success: boolean) => {
      if (success) {
        hilog.info(0x0000, 'testTag', 'server stop service successfully');
        // ···
      } else {
        hilog.error(0x0000, 'testTag', 'server stop service failed');
        // ···
      }
    });
    ```

## Samples

The following samples are provided to help you better understand how to develop WebSocket connection features:

- [WebSocket (ArkTS) (API9)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Connectivity/WebSocket)

- [WebSocket Client Example](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/WebSocket_case)
- [WebSocket Server Example](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/NetWork_Kit/NetWorkKit_Datatransmission/WebSocket_Server_case)
