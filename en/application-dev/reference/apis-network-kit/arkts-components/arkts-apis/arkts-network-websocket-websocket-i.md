# WebSocket

Defines a **WebSocket** object. Before invoking WebSocket APIs, you need to call [webSocket.createWebSocket](arkts-network-websocket-createwebsocket-f.md) to create a **WebSocket** object.

**Since:** 6

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { webSocket } from '@kit.NetworkKit';
```

## close

```TypeScript
close(callback: AsyncCallback<boolean>): void
```

Closes the WebSocket connection. This API uses an asynchronous callback to return the result.

**Since:** 6

**Required permissions:** ohos.permission.INTERNET

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** indicates that the operation is successful, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |

**Examples**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let ws = webSocket.createWebSocket();
ws.close((err: BusinessError) => {
  if (!err) {
    console.info("close success")
  } else {
    console.error(`close fail. Code: ${err.code}, message: ${err.message}`)
  }
});
```

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let ws = webSocket.createWebSocket();

let options: webSocket.WebSocketCloseOptions | undefined;
if (options != undefined) {
    options.code = 1000
    options.reason = "your reason"
}
ws.close(options, (err: BusinessError) => {
    if (!err) {
        console.info("close success")
    } else {
        console.error(`close fail. Code: ${err.code}, message: ${err.message}`)
    }
});
```

```TypeScript
import { webSocket } from '@kit.NetworkKit';

let ws = webSocket.createWebSocket();
let options: webSocket.WebSocketCloseOptions | undefined;
if (options != undefined) {
    options.code = 1000
    options.reason = "your reason"
}
let promise = ws.close();
promise.then((value: boolean) => {
    console.info("close success")
}).catch((err:string) => {
    console.error("close fail, error:" + JSON.stringify(err))
});
```

## close

```TypeScript
close(options: WebSocketCloseOptions, callback: AsyncCallback<boolean>): void
```

Closes the WebSocket connection based on the options parameter. This API uses an asynchronous callback to return the result.

**Since:** 6

**Required permissions:** ohos.permission.INTERNET

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [WebSocketCloseOptions](arkts-network-websocket-websocketcloseoptions-i.md) | Yes | Request options. For details, see [WebSocketCloseOptions](arkts-network-websocket-websocketcloseoptions-i.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** indicates that the operation is successful, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |

**Examples**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let ws = webSocket.createWebSocket();
ws.close((err: BusinessError) => {
  if (!err) {
    console.info("close success")
  } else {
    console.error(`close fail. Code: ${err.code}, message: ${err.message}`)
  }
});
```

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let ws = webSocket.createWebSocket();

let options: webSocket.WebSocketCloseOptions | undefined;
if (options != undefined) {
    options.code = 1000
    options.reason = "your reason"
}
ws.close(options, (err: BusinessError) => {
    if (!err) {
        console.info("close success")
    } else {
        console.error(`close fail. Code: ${err.code}, message: ${err.message}`)
    }
});
```

```TypeScript
import { webSocket } from '@kit.NetworkKit';

let ws = webSocket.createWebSocket();
let options: webSocket.WebSocketCloseOptions | undefined;
if (options != undefined) {
    options.code = 1000
    options.reason = "your reason"
}
let promise = ws.close();
promise.then((value: boolean) => {
    console.info("close success")
}).catch((err:string) => {
    console.error("close fail, error:" + JSON.stringify(err))
});
```

## close

```TypeScript
close(options?: WebSocketCloseOptions): Promise<boolean>
```

Closes a WebSocket connection based on the specified options. This API uses a promise to return the result.

**Since:** 6

**Required permissions:** ohos.permission.INTERNET

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [WebSocketCloseOptions](arkts-network-websocket-websocketcloseoptions-i.md) | No | Request options. For details, see [WebSocketCloseOptions](arkts-network-websocket-websocketcloseoptions-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the operation is successful, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |

**Examples**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let ws = webSocket.createWebSocket();
ws.close((err: BusinessError) => {
  if (!err) {
    console.info("close success")
  } else {
    console.error(`close fail. Code: ${err.code}, message: ${err.message}`)
  }
});
```

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let ws = webSocket.createWebSocket();

let options: webSocket.WebSocketCloseOptions | undefined;
if (options != undefined) {
    options.code = 1000
    options.reason = "your reason"
}
ws.close(options, (err: BusinessError) => {
    if (!err) {
        console.info("close success")
    } else {
        console.error(`close fail. Code: ${err.code}, message: ${err.message}`)
    }
});
```

```TypeScript
import { webSocket } from '@kit.NetworkKit';

let ws = webSocket.createWebSocket();
let options: webSocket.WebSocketCloseOptions | undefined;
if (options != undefined) {
    options.code = 1000
    options.reason = "your reason"
}
let promise = ws.close();
promise.then((value: boolean) => {
    console.info("close success")
}).catch((err:string) => {
    console.error("close fail, error:" + JSON.stringify(err))
});
```

## connect

```TypeScript
connect(url: string, callback: AsyncCallback<boolean>): void
```

Initiates a WebSocket request to establish a WebSocket connection to a given URL. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> The boolean value returned in the callback indicates only whether the connection request is created
> successfully. To detect whether the WebSocket connection is successful, you need to subscribe to the **open**
> event via [on('open')](#onopen) before
> calling this API.
> 
> **NOTE:** 
> 
> The URL cannot contain more than 1024 characters. Otherwise, the connection fails. Since API version 15, the
> maximum length of URLs is changed from 1024 characters to 2048 characters. Since API version 26, the maximum
> length of URLs is changed from 2048 characters to 8196 characters.

**Since:** 6

**Required permissions:** ohos.permission.INTERNET

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | URL for establishing a WebSocket connection. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** indicates that the operation is successful, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [2302999](../errorcode-net-webSocket.md#2302999-internal-error) | Websocket other unknown error.<br>**Applicable version:** 10 and later |
| [2302001](../errorcode-net-webSocket.md#2302001-websocket-url-error) | Websocket url error.<br>**Applicable version:** 12 and later |
| [2302002](../errorcode-net-webSocket.md#2302002-websocket-certificate-does-not-exist) | Websocket certificate file does not exist.<br>**Applicable version:** 12 and later |
| [2302003](../errorcode-net-webSocket.md#2302003-websocket-connection-already-exists) | Websocket connection already exists.<br>**Applicable version:** 12 and later |
| [2302998](../errorcode-net-webSocket.md#2302998-domain-access-denied) | It is not allowed to access this domain.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let ws = webSocket.createWebSocket();
let url = "ws://";
ws.connect(url, (err: BusinessError, value: boolean) => {
  if (!err) {
    console.info("connect success")
  } else {
    console.error(`connect fail. Code: ${err.code}, message: ${err.message}`)
  }
});
```

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Example 1:
let ws = webSocket.createWebSocket();
let options: webSocket.WebSocketRequestOptions | undefined;
if (options !=undefined) {
  options.header = {
     name1: "value1",
     name2: "value2",
     name3: "value3"
  };
  options.caPath = "";
}
let url = "ws://"
ws.connect(url, options, (err: BusinessError, value: Object) => {
  if (!err) {
    console.info("connect success")
  } else {
    console.error(`connect fail. Code: ${err.code}, message: ${err.message}`)
  }
});

// Example 2:
let url = "ws://"
let ws = webSocket.createWebSocket();
let options: webSocket.WebSocketRequestOptions = {
  minSupportTlsProtocol: webSocket.TlsProtocol.TLS_V_1_1
};
ws.connect(url, options, (err: BusinessError, value: Object) => {
  if (!err) {
    console.info("connect success")
  } else {
    console.error(`connect fail. Code: ${err.code}, message: ${err.message}`)
  }
});
```

```TypeScript
import { webSocket } from '@kit.NetworkKit';

let ws = webSocket.createWebSocket();
let url = "ws://"
let promise = ws.connect(url);
promise.then((value: boolean) => {
  console.info("connect success")
}).catch((err:string) => {
  console.error("connect fail, error:" + JSON.stringify(err))
});
```

## connect

```TypeScript
connect(url: string, options: WebSocketRequestOptions, callback: AsyncCallback<boolean>): void
```

Initiates a WebSocket request to establish a WebSocket connection to a given URL. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> The boolean value returned in the callback indicates only whether the connection request is created
> successfully. To detect whether the WebSocket connection is successful, you need to subscribe to the **open**
> event via [on('open')](#onopen) before
> calling this API.
> 
> **NOTE:** 
> 
> The URL cannot contain more than 1024 characters. Otherwise, the connection fails. Since API version 15, the
> maximum length of URLs is changed from 1024 characters to 2048 characters. Since API version 26, the maximum
> length of URLs is changed from 2048 characters to 8196 characters.

**Since:** 6

**Required permissions:** ohos.permission.INTERNET

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | URL for establishing a WebSocket connection. |
| options | [WebSocketRequestOptions](arkts-network-websocket-websocketrequestoptions-i.md) | Yes | Request options. For details, see [WebSocketRequestOptions](arkts-network-websocket-websocketrequestoptions-i.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** indicates that the operation is successful, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [2302999](../errorcode-net-webSocket.md#2302999-internal-error) | Websocket other unknown error.<br>**Applicable version:** 10 and later |
| [2302001](../errorcode-net-webSocket.md#2302001-websocket-url-error) | Websocket url error.<br>**Applicable version:** 12 and later |
| [2302002](../errorcode-net-webSocket.md#2302002-websocket-certificate-does-not-exist) | Websocket certificate file does not exist.<br>**Applicable version:** 12 and later |
| [2302003](../errorcode-net-webSocket.md#2302003-websocket-connection-already-exists) | Websocket connection already exists.<br>**Applicable version:** 12 and later |
| [2302998](../errorcode-net-webSocket.md#2302998-domain-access-denied) | It is not allowed to access this domain.<br>**Applicable version:** 12 and later |

**Examples**

See [connect](#connect)

## connect

```TypeScript
connect(url: string, options?: WebSocketRequestOptions): Promise<boolean>
```

Establishes a WebSocket connection to a given URL. This API uses a promise to return the result.

> **NOTE:** 
> 
> The boolean value returned in the callback indicates only whether the connection request is created
> successfully. To detect whether the WebSocket connection is successful, you need to subscribe to the **open**
> event via [on('open')](#onopen) before
> calling this API.
> 
> **NOTE:** 
> 
> The URL cannot contain more than 1024 characters. Otherwise, the connection fails. Since API version 15, the
> maximum length of URLs is changed from 1024 characters to 2048 characters. Since API version 26, the maximum
> length of URLs is changed from 2048 characters to 8196 characters.

**Since:** 6

**Required permissions:** ohos.permission.INTERNET

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | URL for establishing a WebSocket connection. |
| options | [WebSocketRequestOptions](arkts-network-websocket-websocketrequestoptions-i.md) | No | Request options. For details, see [WebSocketRequestOptions](arkts-network-websocket-websocketrequestoptions-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Callback used to return the result. The value **true** indicates that the operation is successful, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [2302999](../errorcode-net-webSocket.md#2302999-internal-error) | Websocket other unknown error.<br>**Applicable version:** 10 and later |
| [2302001](../errorcode-net-webSocket.md#2302001-websocket-url-error) | Websocket url error.<br>**Applicable version:** 12 and later |
| [2302002](../errorcode-net-webSocket.md#2302002-websocket-certificate-does-not-exist) | Websocket certificate file does not exist.<br>**Applicable version:** 12 and later |
| [2302003](../errorcode-net-webSocket.md#2302003-websocket-connection-already-exists) | Websocket connection already exists.<br>**Applicable version:** 12 and later |
| [2302998](../errorcode-net-webSocket.md#2302998-domain-access-denied) | It is not allowed to access this domain.<br>**Applicable version:** 12 and later |

**Examples**

See [connect](#connect)

## off('open')

```TypeScript
off(type: 'open', callback?: AsyncCallback<Object>): void
```

Unsubscribes from WebSocket open events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> You can pass the callback of the **on** function if you want to cancel listening for a certain type of event.
> If you do not pass the callback, you will cancel listening for all events.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'open' | Yes | Event type.<br> **open**: event indicating that a WebSocket connection has been opened. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Object&gt; | No | Callback used to return the result. |

## off('openInfo')

```TypeScript
off(type: 'openInfo', callback?: AsyncCallback<WebSocketOpenInfo>): void
```

Cancels listening for the open info events of a WebSocket connection.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'openInfo' | Yes | event indicating that the open info of a WebSocket connection is returned. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[WebSocketOpenInfo](arkts-network-websocket-websocketopeninfo-i.md)&gt; | No | the callback used to return the result. |

## off('message')

```TypeScript
off(type: 'message', callback?: AsyncCallback<string | ArrayBuffer>): void
```

Unsubscribes from WebSocket server message receiving events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> The data in **AsyncCallback** can be in the format of string (API version 6) or ArrayBuffer (API version 8).
> 
> You can pass the callback of the **on** function if you want to cancel listening for a certain type of event.
> If you do not pass the callback, you will cancel listening for all events.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'message' | Yes | Event type.<br> **message**: event indicating that a message has been received from the server. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string &#124; ArrayBuffer&gt; | No | Callback used to return the result. |

## off('close')

```TypeScript
off(type: 'close', callback?: AsyncCallback<CloseResult>): void
```

Unsubscribes from WebSocket close events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> You can pass the callback of the **on** function if you want to cancel listening for a certain type of event.
> If you do not pass the callback, you will cancel listening for all events.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'close' | Yes | Event type.<br> **close**: event indicating that a WebSocket connection has been closed. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[CloseResult](arkts-network-websocket-closeresult-i.md)&gt; | No | Callback used to return the result.<br>**close** and **reason** indicate the error code and error cause for closing the connection, respectively. |

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

Unsubscribes from WebSocket error events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> You can pass the callback of the **on** function if you want to cancel listening for a certain type of event.
> If you do not pass the callback, you will cancel listening for all events.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type.<br> **error**: event indicating the WebSocket connection has encountered an error. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | No | Callback used to return the result. |

## off('dataEnd')

```TypeScript
off(type: 'dataEnd', callback?: Callback<void>): void
```

Unsubscribes from WebSocket data receiving end events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> You can pass the callback of the **on** function if you want to cancel listening for a certain type of event.
> If you do not pass the callback, you will cancel listening for all events.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'dataEnd' | Yes | Event type.<br> **dataEnd**: event indicating the data receiving over the WebSocket connection has ended. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | No |  |

## off('headerReceive')

```TypeScript
off(type: 'headerReceive', callback?: Callback<ResponseHeaders>): void
```

Unsubscribes from HTTP response header events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> You can pass the callback of the **on** function if you want to cancel listening for a certain type of event.
> If you do not pass the callback, you will cancel listening for all events.

**Since:** 12

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'headerReceive' | Yes | Event type.<br> Event type. The value is **headerReceive**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ResponseHeaders](arkts-network-websocket-responseheaders-t.md)&gt; | No | Callback used to return the result. |

## on('open')

```TypeScript
on(type: 'open', callback: AsyncCallback<Object>): void
```

Subscribes to WebSocket open events. This API uses an asynchronous callback to return the result. This event indicates whether the WebSocket connection is successful. This API must be called before [connect](#connect) is called to initiate a connection request.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'open' | Yes | Event type.<br> **open**: event indicating that a WebSocket connection has been opened. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Object&gt; | Yes | Callback used to return the result. |

## on('message')

```TypeScript
on(type: 'message', callback: AsyncCallback<string | ArrayBuffer>): void
```

Subscribes to WebSocket server message receiving events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> The data in **AsyncCallback** can be in the format of string (API version 6) or ArrayBuffer (API version 8).

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'message' | Yes | Event type.<br> **message**: event indicating that a message has been received from the server. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string &#124; ArrayBuffer&gt; | Yes | Callback used to return the result. |

## on('openInfo')

```TypeScript
on(type: 'openInfo', callback: AsyncCallback<WebSocketOpenInfo>): void
```

Enables listening for the open info events of a WebSocket connection.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'openInfo' | Yes | event indicating that the open info of a WebSocket connection is returned. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[WebSocketOpenInfo](arkts-network-websocket-websocketopeninfo-i.md)&gt; | Yes | the callback used to return the result. |

## on('close')

```TypeScript
on(type: 'close', callback: AsyncCallback<CloseResult>): void
```

Subscribes to WebSocket close events. This API uses an asynchronous callback to return the result.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'close' | Yes | Event type.<br> **close**: event indicating that a WebSocket connection has been closed. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[CloseResult](arkts-network-websocket-closeresult-i.md)&gt; | Yes | Callback used to return the result.<br>**close** and **reason** indicate the error code and error cause for closing the connection, respectively. |

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

Subscribes to WebSocket error events. This API uses an asynchronous callback to return the result.

The error code of the [error](#onerror) event callback is described as follows: WebSocket is essentially an HTTP protocol upgrade. If the server agrees to the upgrade, the server returns 101. The status code indicates that the protocol is switched from HTTP to WebSocket (the **open** callback is triggered). If the server rejects the upgrade or other exceptions occur, the server returns 200, indicating that the server only processes the request as a common HTTP request.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type.<br> **error**: event indicating the WebSocket connection has encountered an error. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | Yes | Callback used to return the result. |

## on('dataEnd')

```TypeScript
on(type: 'dataEnd', callback: Callback<void>): void
```

Subscribes to the WebSocket data receiving end event. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'dataEnd' | Yes | Event type.<br> **dataEnd**: event indicating the data receiving over the WebSocket connection has ended. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

## on('headerReceive')

```TypeScript
on(type: 'headerReceive', callback: Callback<ResponseHeaders>): void
```

Subscribes to HTTP response header events. This API uses an asynchronous callback to return the result.

**Since:** 12

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'headerReceive' | Yes | Event type.<br> Event type. The value is **headerReceive**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ResponseHeaders](arkts-network-websocket-responseheaders-t.md)&gt; | Yes | Callback used to return the result. |

## send

```TypeScript
send(data: string | ArrayBuffer, callback: AsyncCallback<boolean>): void
```

Sends data through a WebSocket connection. This API uses an asynchronous callback to return the result.

**Since:** 6

**Required permissions:** ohos.permission.INTERNET

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string &#124; ArrayBuffer | Yes | Data to send.<br>Only the string type is supported for API version 6 or earlier. Both the string and ArrayBuffer types are supported for API version 8 or later. A maximum of 5,242,864 bytes (that is, 5 x 1024 x 1024 - 16) can be sent. If the data size exceeds the upper limit, error code 401 will be returned. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** indicates that the operation is successful, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |

**Examples**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let ws = webSocket.createWebSocket();
let url = "ws://"
class OutValue {
  status: number = 0
  message: string = ""
}
ws.connect(url, (err: BusinessError, value: boolean) => {
    if (!err) {
      console.info("connect success")
    } else {
      console.error(`connect fail. Code: ${err.code}, message: ${err.message}`)
    }
});
ws.on('open', (err: BusinessError, value: Object) => {
  console.info("on open, status:" + (value as OutValue).status + ", message:" + (value as OutValue).message)
    ws.send("Hello, server!", (err: BusinessError, value: boolean) => {
    if (!err) {
      console.info("send success")
    } else {
      console.error(`send fail. Code: ${err.code}, message: ${err.message}`)
    }
  });
});
```

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let ws = webSocket.createWebSocket();
let url = "ws://"
class OutValue {
  status: number = 0
  message: string = ""
}
ws.connect(url, (err: BusinessError, value: boolean) => {
    if (!err) {
      console.info("connect success")
    } else {
      console.error("connect fail. Code: ${err.code}, message: ${err.message}")
    }
});

ws.on('open', (err: BusinessError, value: Object) => {
  console.info("on open, status:" + (value as OutValue).status + ", message:" + (value as OutValue).message)
  let promise = ws.send("Hello, server!");
  promise.then((value: boolean) => {
    console.info("send success")
  }).catch((err:string) => {
    console.error("send fail, error:" + JSON.stringify(err))
  });
});
```

## send

```TypeScript
send(data: string | ArrayBuffer): Promise<boolean>
```

Sends data through the WebSocket connection. This API uses a promise to return the result.

**Since:** 6

**Required permissions:** ohos.permission.INTERNET

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string &#124; ArrayBuffer | Yes | Data to send.<br>Only the string type is supported for API version 6 or earlier. Both the string and ArrayBuffer types are supported for API version 8 or later. A maximum of 5,242,864 bytes (that is, 5 x 1024 x 1024 - 16) can be sent. If the data size exceeds the upper limit, error code 401 will be returned. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the operation is successful, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |

**Examples**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let ws = webSocket.createWebSocket();
let url = "ws://"
class OutValue {
  status: number = 0
  message: string = ""
}
ws.connect(url, (err: BusinessError, value: boolean) => {
    if (!err) {
      console.info("connect success")
    } else {
      console.error(`connect fail. Code: ${err.code}, message: ${err.message}`)
    }
});
ws.on('open', (err: BusinessError, value: Object) => {
  console.info("on open, status:" + (value as OutValue).status + ", message:" + (value as OutValue).message)
    ws.send("Hello, server!", (err: BusinessError, value: boolean) => {
    if (!err) {
      console.info("send success")
    } else {
      console.error(`send fail. Code: ${err.code}, message: ${err.message}`)
    }
  });
});
```

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let ws = webSocket.createWebSocket();
let url = "ws://"
class OutValue {
  status: number = 0
  message: string = ""
}
ws.connect(url, (err: BusinessError, value: boolean) => {
    if (!err) {
      console.info("connect success")
    } else {
      console.error("connect fail. Code: ${err.code}, message: ${err.message}")
    }
});

ws.on('open', (err: BusinessError, value: Object) => {
  console.info("on open, status:" + (value as OutValue).status + ", message:" + (value as OutValue).message)
  let promise = ws.send("Hello, server!");
  promise.then((value: boolean) => {
    console.info("send success")
  }).catch((err:string) => {
    console.error("send fail, error:" + JSON.stringify(err))
  });
});
```
