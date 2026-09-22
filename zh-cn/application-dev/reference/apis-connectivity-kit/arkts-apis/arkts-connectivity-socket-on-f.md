# on

## 导入模块

```TypeScript
import { socket } from '@kit.ConnectivityKit';
```

## on('sppRead')

```TypeScript
function on(type: 'sppRead', clientSocket: number, callback: Callback<ArrayBuffer>): void
```

客户端和服务端均可使用，订阅套接字读请求事件。调用该接口后，当收到对端发送的数据会执行订阅的回调函数。

若客户端使用，需在调用[socket.sppConnect](arkts-connectivity-socket-sppconnect-f.md)后，且连接成功后使用。若服务端使用，需在调用[socket.sppAccept](arkts-connectivity-socket-sppaccept-f.md)后，且连接成功后使用。不可以和API version 18开始支持的[socket.sppReadAsync](arkts-connectivity-socket-sppreadasync-f.md)接口混用，同一路套接字连接只能使用socket.on('sppRead')接口或者[socket.sppReadAsync](arkts-connectivity-socket-sppreadasync-f.md)接口。若开发者需感知传输过程中异常断连等错误，建议使用[socket.sppReadAsync](arkts-connectivity-socket-sppreadasync-f.md)。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sppRead' | 是 | 事件回调类型，支持的事件为'sppRead'，表示订阅spp读请求事件。当收到了对端发送的数据时，触发该事件。 |
| clientSocket | number | 是 | 客户端套接字的ID。该值是调用[socket.sppAccept](arkts-connectivity-socket-sppaccept-f.md)或[socket.sppConnect](arkts-connectivity-socket-sppconnect-f.md)接口，通过其异步callback获取到的。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;ArrayBuffer&gt; | 是 | 指定订阅的回调函数，会返回读取到的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2901054](../errorcode-bluetoothManager.md#2901054-io传输失败) | IO error. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let clientNumber = 1; // 入参clientNumber由sppAccept或sppConnect接口获取。
let dataRead = (dataBuffer: ArrayBuffer) => {
    let data = new Uint8Array(dataBuffer);
    console.info('bluetooth data length is: ' + data.byteLength);
}
try {
    socket.on('sppRead', clientNumber, dataRead);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
