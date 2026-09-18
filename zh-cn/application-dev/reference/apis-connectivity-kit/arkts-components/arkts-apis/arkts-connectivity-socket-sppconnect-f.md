# sppConnect

## 导入模块

```TypeScript
import { socket } from '@kit.ConnectivityKit';
```

## sppConnect

```TypeScript
function sppConnect(deviceId: string, options: SppOptions, callback: AsyncCallback<number>): void
```

客户端使用，创建一个客户端套接字，并向服务端的特定服务发起连接请求。

通过[SppOptions](arkts-connectivity-socket-sppoptions-i.md)参数的type表示需要连接的服务类型。需确保服务端设备已具备需要连接的服务。服务端可通过[socket.sppListen](arkts-connectivity-socket-spplisten-f.md)注册并监听连接请求。连接建立成功后，即可通过[socket.sppWrite](arkts-connectivity-socket-sppwrite-f.md)或[socket.sppWriteAsync](arkts-connectivity-socket-sppwriteasync-f.md)接口，同服务端进行数据传输。当客户端不再需要已建立的连接时，可通过[socket.sppCloseClientSocket](arkts-connectivity-socket-sppcloseclientsocket-f.md)主动断开连接。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 对端设备地址，例如："XX:XX:XX:XX:XX:XX"。 |
| options | [SppOptions](arkts-connectivity-socket-sppoptions-i.md) | 是 | 客户端套接字连接配置参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当客户端发起连接成功，err为undefined，data为当前客户端套接字的ID，有效值为非负值；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900004](../errorcode-bluetoothManager.md#2900004-配置文件不支持) | Profile not supported. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let clientSocket = (code: BusinessError, number: number) => {
  if (code) {
    console.error('sppConnect error, code is ' + code);
    return;
  } else {
    // 获取的number用作客户端后续读/写操作的socket id。
    console.info('bluetooth clientSocket Number: ' + number);
  }
}

// 以RFCOMM链路类型套接字为例
let sppOption:socket.SppOptions = {uuid: '00001810-0000-1000-8000-00805F9B34FB', secure: false, type: socket.SppType.SPP_RFCOMM};
try {
    socket.sppConnect('XX:XX:XX:XX:XX:XX', sppOption, clientSocket);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
