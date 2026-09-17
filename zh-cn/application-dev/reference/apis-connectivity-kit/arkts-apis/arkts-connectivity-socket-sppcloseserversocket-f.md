# sppCloseServerSocket

## 导入模块

```TypeScript
import { socket } from '@kit.ConnectivityKit';
```

## sppCloseServerSocket

```TypeScript
function sppCloseServerSocket(socket: number): void
```

服务端使用，删除指定的服务端套接字。

需先调用[socket.sppListen](arkts-connectivity-socket-spplisten-f.md)并获取到有效的服务端监听套接字标识符。若服务端无需继续监听，可调用本接口以关闭监听套接字，蓝牙子系统会删除此前注册的服务。如果此时客户端发起连接，就会连接失败。若服务端此时与其他客户端存在连接，该接口调用后，也会主动断开与客户端的连接。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| socket | number | 是 | 服务端监听套接字的ID。该值是调用[socket.sppListen](arkts-connectivity-socket-spplisten-f.md)接口，通过其异步callback获取到的。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let serverNumber = 1; // 此处serverNumber需赋值为调用sppListen接口后，在回调中得到的serverNumber。
try {
    socket.sppCloseServerSocket(serverNumber);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
