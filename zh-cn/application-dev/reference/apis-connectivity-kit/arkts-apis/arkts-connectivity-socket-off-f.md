# off

## 导入模块

```TypeScript
import { socket } from '@kit.ConnectivityKit';
```

## off('sppRead')

```TypeScript
function off(type: 'sppRead', clientSocket: number, callback?: Callback<ArrayBuffer>): void
```

取消订阅套接字读请求事件。

须在调用[socket.on('sppRead')](arkts-connectivity-socket-on-f.md#onsppread)成功订阅后，才能调用该接口取消订阅。若客户端使用，需在调用[socket.sppConnect](arkts-connectivity-socket-sppconnect-f.md)后，且连接成功后使用。若服务端使用，需在调用[socket.sppAccept](arkts-connectivity-socket-sppaccept-f.md)后，且连接成功后使用。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sppRead' | 是 | 事件回调类型，支持的事件为'sppRead'，表示取消订阅spp读请求事件。 |
| clientSocket | number | 是 | 客户端套接字的ID。该值是调用[socket.sppAccept](arkts-connectivity-socket-sppaccept-f.md)或[socket.sppConnect](arkts-connectivity-socket-sppconnect-f.md)接口，通过其异步callback获取到的。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;ArrayBuffer&gt; | 否 | 指定取消订阅的回调函数通知。若传参，则需与[socket.on('sppRead')](arkts-connectivity-socket-on-f.md#onsppread)中的回调函数一致；若无传参，则取消订阅该type对应的所有回调函数通知。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let clientNumber = 1; // 入参clientNumber由sppAccept或sppConnect接口获取。
try {
    socket.off('sppRead', clientNumber);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
