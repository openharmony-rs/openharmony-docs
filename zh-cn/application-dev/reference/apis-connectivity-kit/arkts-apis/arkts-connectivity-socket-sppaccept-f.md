# sppAccept

## 导入模块

```TypeScript
import { socket } from '@kit.ConnectivityKit';
```

## sppAccept

```TypeScript
function sppAccept(serverSocket: number, callback: AsyncCallback<number>): void
```

服务端使用，接受客户端的套接字连接请求。使用Callback异步回调。

须在调用[socket.sppListen](arkts-connectivity-socket-spplisten-f.md)创建服务端套接字成功后，才能调用该接口监听客户端的连接请求。客户端可通过[socket.sppConnect](arkts-connectivity-socket-sppconnect-f.md)向该服务端发起连接请求。连接建立成功后，即可通过[socket.sppWrite](arkts-connectivity-socket-sppwrite-f.md)、[socket.sppWriteAsync](arkts-connectivity-socket-sppwriteasync-f.md)、[socket.sppReadAsync](arkts-connectivity-socket-sppreadasync-f.md)等接口，与客户端进行数据传输。当服务端不再需要已建立的连接时，可通过[socket.sppCloseClientSocket](arkts-connectivity-socket-sppcloseclientsocket-f.md)主动断开指定的客户端套接字连接。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| serverSocket | number | 是 | 服务端套接字的ID。该值是调用[socket.sppListen](arkts-connectivity-socket-spplisten-f.md)接口后，通过其异步callback获取到的。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当收到客户端的连接请求且连接建立成功时，err为undefined，data是用于标识发起此次连接请求的客户端套接字ID，有效值为非负值；否则err为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900004](../errorcode-bluetoothManager.md#2900004-配置文件不支持) | Profile not supported. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let clientNumber = -1;
let serverNumber = 1;
let acceptClientSocket = (code: BusinessError, number: number) => {
  if (code) {
    console.error('sppListen error, code is ' + code);
    return;
  } else {
    clientNumber = number; // 获取的clientNumber用作客户端后续读/写操作socket的id。
    console.info('sppListen success, clientNumber = ' + clientNumber);
  }
}
try {
    socket.sppAccept(serverNumber, acceptClientSocket); // serverNumber是sppListen回调中得到的serverNumber。
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
