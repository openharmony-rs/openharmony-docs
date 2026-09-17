# sppWriteAsync

## 导入模块

```TypeScript
import { socket } from '@kit.ConnectivityKit';
```

## sppWriteAsync

```TypeScript
function sppWriteAsync(clientSocket: number, data: ArrayBuffer): Promise<void>
```

客户端和服务端均可使用，向对端设备发送数据。使用Promise异步回调。当连接断开时，该接口会抛出错误码并返回。

仅在双方成功建立连接后，调用本接口才有效。若客户端使用，需在调用[socket.sppConnect](arkts-connectivity-socket-sppconnect-f.md)后，且连接成功后使用。若服务端使用，需在调用[socket.sppAccept](arkts-connectivity-socket-sppaccept-f.md)后，且连接成功后使用。按照蓝牙协议规范，数据通道在空闲状态需进入休眠模式以降低功耗。蓝牙子系统实现上，通道在5-7s内没有数据交互时会进入休眠模式，将导致下次调用此接口发送数据前，会耗费500ms左右退出休眠模式才开始发送数据。若想减少每次发送数据前退出休眠模式的耗时，建议每3s左右可往数据通道上发送一次任意大小的心跳数据，对数据通道进行保活，可防止进入休眠模式，但同时也会提高设备功耗。

**起始版本：** 18

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| clientSocket | number | 是 | 客户端套接字的ID。该值是调用[sppAccept](arkts-connectivity-socket-sppaccept-f.md)或[sppConnect](arkts-connectivity-socket-sppconnect-f.md)接口，通过其异步callback获取到的。 |
| data | ArrayBuffer | 是 | 写入的数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2901054](../errorcode-bluetoothManager.md#2901054-io传输失败) | IO error. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let clientNumber = 1; // 入参clientNumber由sppAccept或sppConnect接口获取。
let arrayBuffer = new ArrayBuffer(8);
let data = new Uint8Array(arrayBuffer);
try {
    socket.sppWriteAsync(clientNumber, arrayBuffer).then(() => {
      console.info("sppWrite success");
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
