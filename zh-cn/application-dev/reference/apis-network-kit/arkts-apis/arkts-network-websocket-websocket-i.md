# WebSocket

在调用WebSocket的方法前，需要先通过[webSocket.createWebSocket](arkts-network-websocket-createwebsocket-f.md)创建一个WebSocket。

**起始版本：** 6

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
```

## close

```TypeScript
close(callback: AsyncCallback<boolean>): void
```

关闭WebSocket连接，使用callback异步回调。

**起始版本：** 6

**需要权限：** ohos.permission.INTERNET

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。true:关闭请求创建成功；false:关闭请求创建失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

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

## close

```TypeScript
close(options: WebSocketCloseOptions, callback: AsyncCallback<boolean>): void
```

根据参数options，关闭WebSocket连接，使用callback异步回调。

**起始版本：** 6

**需要权限：** ohos.permission.INTERNET

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [WebSocketCloseOptions](arkts-network-websocket-websocketcloseoptions-i.md) | 是 | 参考[WebSocketCloseOptions](arkts-network-websocket-websocketcloseoptions-i.md)。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。true:关闭请求创建成功；false:关闭请求创建失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

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

## close

```TypeScript
close(options?: WebSocketCloseOptions): Promise<boolean>
```

根据可选参数code和reason，关闭WebSocket连接。使用Promise异步回调。

**起始版本：** 6

**需要权限：** ohos.permission.INTERNET

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [WebSocketCloseOptions](arkts-network-websocket-websocketcloseoptions-i.md) | 否 | 参考[WebSocketCloseOptions](arkts-network-websocket-websocketcloseoptions-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;boolean & gt; | 以Promise形式返回关闭连接的结果。true:关闭请求创建成功；false:关闭请求创建失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

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

根据URL地址，建立一个WebSocket连接，使用callback异步回调。

> **说明：**
> 
> callback中返回的boolean值仅表示连接请求创建是否成功。如需感知WebSocket是否连接成功，需要在调用该接口前调用
> on('open')订阅open事件。
> 
> **注意：**
> 
> URL地址长度不能超过1024个字符，否则会连接失败。从API version 15开始，URL地址长度限制由1024修改为2048。从API version 26开始，URL地址长度限制由2048修改为8196。

**起始版本：** 6

**需要权限：** ohos.permission.INTERNET

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 建立WebSocket连接的URL地址。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。true:连接请求创建成功；false:连接请求创建失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2302999](../errorcode-net-webSocket.md#2302999-内部错误) | Websocket other unknown error.<br>**适用版本：** 10+ |
| [2302001](../errorcode-net-webSocket.md#2302001-websocket-url错误) | Websocket url error.<br>**适用版本：** 12+ |
| [2302002](../errorcode-net-webSocket.md#2302002-websocket-证书不存在) | Websocket certificate file does not exist.<br>**适用版本：** 12+ |
| [2302003](../errorcode-net-webSocket.md#2302003-websocket-连接已经存在) | Websocket connection already exists.<br>**适用版本：** 12+ |
| [2302998](../errorcode-net-webSocket.md#2302998-不允许访问域名) | It is not allowed to access this domain.<br>**适用版本：** 12+ |

**示例**

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

## connect

```TypeScript
connect(url: string, options: WebSocketRequestOptions, callback: AsyncCallback<boolean>): void
```

根据URL地址，建立一个WebSocket连接，使用callback异步回调。

> **说明：**
> 
> callback中返回的boolean值仅表示连接请求创建是否成功。如需感知WebSocket是否连接成功，需要在调用该接口前调用
> on('open')订阅open事件。
> 
> **注意：**
> 
> URL地址长度不能超过1024个字符，否则会连接失败。从API version 15开始，URL地址长度限制由1024修改为2048。从API version 26开始，URL地址长度限制由2048修改为8196。

**起始版本：** 6

**需要权限：** ohos.permission.INTERNET

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 建立WebSocket连接的URL地址。 |
| options | [WebSocketRequestOptions](arkts-network-websocket-websocketrequestoptions-i.md) | 是 | 参考[WebSocketRequestOptions](arkts-network-websocket-websocketrequestoptions-i.md) 。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。true:连接请求创建成功；false:连接请求创建失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2302999](../errorcode-net-webSocket.md#2302999-内部错误) | Websocket other unknown error.<br>**适用版本：** 10+ |
| [2302001](../errorcode-net-webSocket.md#2302001-websocket-url错误) | Websocket url error.<br>**适用版本：** 12+ |
| [2302002](../errorcode-net-webSocket.md#2302002-websocket-证书不存在) | Websocket certificate file does not exist.<br>**适用版本：** 12+ |
| [2302003](../errorcode-net-webSocket.md#2302003-websocket-连接已经存在) | Websocket connection already exists.<br>**适用版本：** 12+ |
| [2302998](../errorcode-net-webSocket.md#2302998-不允许访问域名) | It is not allowed to access this domain.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 示例1：
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

// 示例2：
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

## connect

```TypeScript
connect(url: string, options?: WebSocketRequestOptions): Promise<boolean>
```

根据URL地址和header，建立一个WebSocket连接。使用Promise异步回调。

> **说明：**
> 
> callback中返回的boolean值仅表示连接请求创建是否成功。如需感知WebSocket是否连接成功，需要在调用该接口前调用
> on('open')订阅open事件。
> 
> **注意：**
> 
> URL地址长度不能超过1024个字符，否则会连接失败。从API version 15开始，URL地址长度限制由1024修改为2048。从API version 26开始，URL地址长度限制由2048修改为8196。

**起始版本：** 6

**需要权限：** ohos.permission.INTERNET

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 建立WebSocket连接的URL地址。 |
| options | [WebSocketRequestOptions](arkts-network-websocket-websocketrequestoptions-i.md) | 否 | 参考[WebSocketRequestOptions](arkts-network-websocket-websocketrequestoptions-i.md) 。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;boolean & gt; | 回调函数。true:连接请求创建成功；false:连接请求创建失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2302999](../errorcode-net-webSocket.md#2302999-内部错误) | Websocket other unknown error.<br>**适用版本：** 10+ |
| [2302001](../errorcode-net-webSocket.md#2302001-websocket-url错误) | Websocket url error.<br>**适用版本：** 12+ |
| [2302002](../errorcode-net-webSocket.md#2302002-websocket-证书不存在) | Websocket certificate file does not exist.<br>**适用版本：** 12+ |
| [2302003](../errorcode-net-webSocket.md#2302003-websocket-连接已经存在) | Websocket connection already exists.<br>**适用版本：** 12+ |
| [2302998](../errorcode-net-webSocket.md#2302998-不允许访问域名) | It is not allowed to access this domain.<br>**适用版本：** 12+ |

**示例**

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

## off('open')

```TypeScript
off(type: 'open', callback?: AsyncCallback<Object>): void
```

取消订阅WebSocket的打开事件，使用callback异步回调。

> **说明：**
> 
> 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'open' | 是 | 取消订阅的事件类型。'open'：WebSocket的打开事件。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Object&gt; | 否 | 回调函数。 |

**示例**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let ws = webSocket.createWebSocket();
class OutValue {
  status: number = 0
  message: string = ""
}
let callback1 = (err: BusinessError, value: Object) => {
 console.info("on open, status:" + ((value as OutValue).status + ", message:" + (value as OutValue).message))
}
ws.on('open', callback1);
// 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。
ws.off('open', callback1);
```

## off('openInfo')

```TypeScript
off(type: 'openInfo', callback?: AsyncCallback<WebSocketOpenInfo>): void
```

取消订阅WebSocket的打开信息事件，使用callback异步回调。

> **说明：**
> 
> 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'openInfo' | 是 | 取消订阅的事件类型。'openInfo'：WebSocket的打开信息事件。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[WebSocketOpenInfo](arkts-network-websocket-websocketopeninfo-i.md)&gt; | 否 | 回调函数。 |

**示例**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let ws = webSocket.createWebSocket();
let callback1 = (err: BusinessError, value: webSocket.WebSocketOpenInfo) => {
  if (value?.protocol != undefined) {
    console.info(`on openInfo exist protocol: status: ${value.status}, message: ${value.message}, protocol: ${value.protocol}`);
  } else {
    console.info(`on openInfo , status: ${value.status}, message: ${value.message}, protocol: ${value.protocol}`);
  }
}
ws.on('openInfo', callback1);
// 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。
ws.off('openInfo', callback1);
```

## off('message')

```TypeScript
off(type: 'message', callback?: AsyncCallback<string | ArrayBuffer>): void
```

取消订阅WebSocket的接收服务器消息事件，使用callback异步回调。

> **说明：**
> 
> AsyncCallback中的数据可以是字符串(API 6)或ArrayBuffer(API 8)。
> 
> 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'message' | 是 | 取消订阅的事件类型。'message'：WebSocket的接收到服务器消息事件。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string \| ArrayBuffer & gt; | 否 | 回调函数。 |

**示例**

```TypeScript
import { webSocket } from '@kit.NetworkKit';

let ws = webSocket.createWebSocket();
ws.off('message');
```

## off('close')

```TypeScript
off(type: 'close', callback?: AsyncCallback<CloseResult>): void
```

取消订阅WebSocket的关闭事件，使用callback异步回调。

> **说明：**
> 
> 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'close' | 是 | 取消订阅的事件类型。'close'：WebSocket的关闭事件。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[CloseResult](arkts-network-websocket-closeresult-i.md)&gt; | 否 | 回调函数。 close：close错误码，reason：错误码说明 |

**示例**

```TypeScript
import { webSocket } from '@kit.NetworkKit';

let ws = webSocket.createWebSocket();
ws.off('close');
```

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

取消订阅WebSocket的Error事件，使用callback异步回调。

> **说明：**
> 
> 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 取消订阅的事件类型。'error'：WebSocket的Error事件。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 否 | 回调函数。 |

**示例**

```TypeScript
import { webSocket } from '@kit.NetworkKit';

let ws = webSocket.createWebSocket();
ws.off('error');
```

## off('dataEnd')

```TypeScript
off(type: 'dataEnd', callback?: Callback<void>): void
```

取消订阅WebSocket的数据接收结束事件，使用callback异步回调。

> **说明：**
> 
> 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。

**起始版本：** 11

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'dataEnd' | 是 | 取消订阅的事件类型。'dataEnd'：WebSocket的数据接收结束事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 否 |  |

**示例**

```TypeScript
import { webSocket } from '@kit.NetworkKit';

let ws = webSocket.createWebSocket();
ws.off('dataEnd');
```

## off('headerReceive')

```TypeScript
off(type: 'headerReceive', callback?: Callback<ResponseHeaders>): void
```

取消订阅HTTP Response Header事件，使用callback异步回调。

> **说明：**
> 
> 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。

**起始版本：** 12

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'headerReceive' | 是 | 取消订阅的事件类型。'headerReceive'：WebSocket的headerReceive事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ResponseHeaders](arkts-network-websocket-responseheaders-t.md)&gt; | 否 | 回调函数，返回订阅事件。 |

**示例**

```TypeScript
import { webSocket } from '@kit.NetworkKit';

let ws = webSocket.createWebSocket();
ws.off('headerReceive');
```

## on('open')

```TypeScript
on(type: 'open', callback: AsyncCallback<Object>): void
```

订阅WebSocket的打开事件，使用callback异步回调。该事件用于指示WebSocket是否连接成功。该接口需要在调用 [connect](#connect)发起连接请求前调用。

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'open' | 是 | 订阅的事件类型。'open'：WebSocket的打开事件。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Object&gt; | 是 | 回调函数。 |

**示例**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError, Callback } from '@kit.BasicServicesKit';

let ws= webSocket.createWebSocket();
class OutValue {
  status: number = 0
  message: string = ""
}
ws.on('open', (err: BusinessError, value: Object) => {
  console.info("on open, status:" + (value as OutValue).status + ", message:" + (value as OutValue).message)
});
```

## on('message')

```TypeScript
on(type: 'message', callback: AsyncCallback<string | ArrayBuffer>): void
```

订阅WebSocket的接收服务器消息事件，使用callback异步回调。

> **说明：**
> 
> AsyncCallback中的数据可以是字符串（API version 6开始支持）或ArrayBuffer（API version 8开始支持）。

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'message' | 是 | 订阅的事件类型。'message'：WebSocket的接收服务器消息事件。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string \| ArrayBuffer & gt; | 是 | 回调函数。 |

**示例**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let ws = webSocket.createWebSocket();
ws.on('message', (err: BusinessError<void>, value: string | ArrayBuffer) => {
  console.info("on message, message:" + value)
});
```

## on('openInfo')

```TypeScript
on(type: 'openInfo', callback: AsyncCallback<WebSocketOpenInfo>): void
```

订阅WebSocket的打开信息事件，使用callback异步回调。该事件用于获取WebSocket连接成功后的详细信息。该接口需要在调用 [connect](#connect)发起连接请求前调用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'openInfo' | 是 | 订阅的事件类型。'openInfo'：WebSocket的打开信息事件。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[WebSocketOpenInfo](arkts-network-websocket-websocketopeninfo-i.md)&gt; | 是 | 回调函数。返回WebSocket连接的详细信息。 |

**示例**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError, Callback } from '@kit.BasicServicesKit';

let ws = webSocket.createWebSocket();
ws.on('openInfo', (err: BusinessError, value: webSocket.WebSocketOpenInfo) => {
  if (value?.protocol != undefined) {
    console.info(`on openInfo exist protocol: status: ${value.status}, message: ${value.message}, protocol: ${value.protocol}`);
  } else {
    console.info(`on openInfo , status: ${value.status}, message: ${value.message}, protocol: ${value.protocol}`);
  }
});
```

## on('close')

```TypeScript
on(type: 'close', callback: AsyncCallback<CloseResult>): void
```

订阅WebSocket的关闭事件，使用callback异步回调。

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'close' | 是 | 订阅的事件类型。'close'：WebSocket的关闭事件。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[CloseResult](arkts-network-websocket-closeresult-i.md)&gt; | 是 | 回调函数。 close：close错误码，reason：错误码说明 |

**示例**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let ws = webSocket.createWebSocket();
ws.on('close', (err: BusinessError, value: webSocket.CloseResult) => {
  console.info("on close, code is " + value.code + ", reason is " + value.reason)
});
```

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

订阅WebSocket的Error事件，使用callback异步回调。关于[error](#onerror)事件回调的错误码说明：WebSocket的本质是HTTP协议升级，若 服务器同意升级，服务器会返回101。状态码表示协议从HTTP切换为WebSocket协议（触发open回调），而如果服务器拒绝了升级或出现其他异常，则返回200，表示服务器只是将请求当作普通的HTTP请求来处理。

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 订阅的事件类型。'error'：WebSocket的Error事件。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 是 | 回调函数。 |

**示例**

```TypeScript
import { webSocket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let ws = webSocket.createWebSocket();
ws.on('error', (err: BusinessError) => {
  console.error(`on error. Code: ${err.code}, message: ${err.message}`)
});
```

## on('dataEnd')

```TypeScript
on(type: 'dataEnd', callback: Callback<void>): void
```

订阅WebSocket的数据接收结束事件，使用callback异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'dataEnd' | 是 | 订阅的事件类型。'dataEnd'：WebSocket的数据接收结束事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 回调函数。 |

**示例**

```TypeScript
import { webSocket } from '@kit.NetworkKit';

let ws = webSocket.createWebSocket();
ws.on('dataEnd', () => {
  console.info("on dataEnd")
});
```

## on('headerReceive')

```TypeScript
on(type: 'headerReceive', callback: Callback<ResponseHeaders>): void
```

订阅HTTP Response Header事件，使用callback异步回调。

**起始版本：** 12

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'headerReceive' | 是 | 订阅的事件类型。'headerReceive'：WebSocket的headerReceive事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ResponseHeaders](arkts-network-websocket-responseheaders-t.md)&gt; | 是 | 回调函数，返回订阅事件。 |

**示例**

```TypeScript
import { webSocket } from '@kit.NetworkKit';

let ws = webSocket.createWebSocket();
ws.on('headerReceive', (data) => {
  console.info("on headerReceive " + JSON.stringify(data))
});
```

## send

```TypeScript
send(data: string | ArrayBuffer, callback: AsyncCallback<boolean>): void
```

通过WebSocket连接发送数据，使用callback异步回调。

**起始版本：** 6

**需要权限：** ohos.permission.INTERNET

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string \| ArrayBuffer | 是 | 发送的数据。 API 6及更早版本仅支持string类型。API 8起同时支持string和ArrayBuffer类型。最大支持发送5242864字节数据(即5 * 1024 * 1024 - 16)，超过该大小会返回401 错误码。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。true:发送请求创建成功；false:发送请求创建失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

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

## send

```TypeScript
send(data: string | ArrayBuffer): Promise<boolean>
```

通过WebSocket连接发送数据。使用Promise异步回调。

**起始版本：** 6

**需要权限：** ohos.permission.INTERNET

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string \| ArrayBuffer | 是 | 发送的数据。 API 6及更早版本仅支持string类型。API 8起同时支持string和ArrayBuffer类型。最大支持发送5242864字节数据(即5 * 1024 * 1024 - 16)，超过该大小会返回401 错误码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;boolean & gt; | 以Promise形式返回发送数据的结果。true:发送请求创建成功；false:发送请求创建失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

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
