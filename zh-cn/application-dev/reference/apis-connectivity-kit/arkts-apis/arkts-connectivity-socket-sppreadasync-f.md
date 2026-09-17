# sppReadAsync

## 导入模块

```TypeScript
import { socket } from '@kit.ConnectivityKit';
```

## sppReadAsync

```TypeScript
function sppReadAsync(clientSocket: number): Promise<ArrayBuffer>
```

客户端和服务端均可使用，读取对端发送数据的异步接口。使用Promise异步回调。当连接断开时，该接口会抛出错误码并返回。

若客户端使用，需在调用[socket.sppConnect](arkts-connectivity-socket-sppconnect-f.md)后，且连接成功后使用。若服务端使用，需在调用[socket.sppAccept](arkts-connectivity-socket-sppaccept-f.md)后，且连接成功后使用。不可以和API version 10开始支持的[socket.on('sppRead')](arkts-connectivity-socket-on-f.md#onsppread)接口混用，同一路socket只能使用[socket.on('sppRead')](arkts-connectivity-socket-on-f.md#onsppread)接口或者socket.sppReadAsync接口。通过Promise异步返回读取的数据，建议在连接成功后循环调用去获取接收到的数据，若不及时调用会丢失接收的数据。该接口为异步接口，需要等异步回调结果返回后才能进行下一次调用。

**起始版本：** 18

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| clientSocket | number | 是 | 客户端套接字的ID。该值是调用[sppAccept](arkts-connectivity-socket-sppaccept-f.md)或[sppConnect](arkts-connectivity-socket-sppconnect-f.md)接口，通过其异步callback获取到的。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ArrayBuffer&gt; | Promise对象。返回读取的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2901054](../errorcode-bluetoothManager.md#2901054-io传输失败) | IO error. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 入参clientNumber由sppAccept或sppConnect接口获取。
async function readAsync(clientNumber: number) {
  let flag = 1;
  try {
    while (flag) { // 该接口需业务循环调用读取，具体循环形式按业务需要来实现，这里只是示例。
      let buffer = await socket.sppReadAsync(clientNumber); // 使用await确保顺序读取。
      let data = new Uint8Array(buffer);
      if (data) {
        console.info('sppRead success, data length = ' + data.byteLength);
        // 在此处理接收到的数据。
      }
    }
  } catch (err) {
    console.error('startSppRead errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
    socket.sppCloseClientSocket(clientNumber); // 发生错误时关闭连接。
  }
}
```
