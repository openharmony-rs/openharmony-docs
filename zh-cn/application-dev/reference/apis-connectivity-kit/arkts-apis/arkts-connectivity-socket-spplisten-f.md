# sppListen

## 导入模块

```TypeScript
import { socket } from '@kit.ConnectivityKit';
```

## sppListen

```TypeScript
function sppListen(name: string, options: SppOptions, callback: AsyncCallback<number>): void
```

服务端使用，创建一个服务端监听套接字。使用Callback异步回调。

通过入参[socket.SppOptions](arkts-connectivity-socket-sppoptions-i.md)的type参数，可以创建不同链路类型的服务端套接字，适用于不同的场景。该操作会在蓝牙子系统中注册对应的服务，表示服务端支持的能力。客户端可通过[socket.sppConnect](arkts-connectivity-socket-sppconnect-f.md)向该服务端发起连接请求。当应用不再需要该服务端套接字时，需通过[socket.sppCloseServerSocket](arkts-connectivity-socket-sppcloseserversocket-f.md)主动关闭创建时获取到的套接字，蓝牙子系统会删除此前注册的服务。如果此时客户端发起连接，就会连接失败。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 服务的名称，该字符串的字符个数范围为[0, 256]。 |
| options | [SppOptions](arkts-connectivity-socket-sppoptions-i.md) | 是 | 用于监听的套接字配置参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当创建服务端套接字成功，err为undefined，data为获取到的服务端套接字的ID，有效值为非负值；否则为错误对象。 |

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

let serverNumber = -1;
let serverSocket = (code: BusinessError, number: number) => {
  if (code) {
    console.error('sppListen error, code is ' + code);
    return;
  } else {
    serverNumber = number;
    console.info('sppListen success, serverNumber = ' + serverNumber);
  }
}

// 以RFCOMM链路类型套接字为例
let sppOption:socket.SppOptions = {uuid: '00001810-0000-1000-8000-00805F9B34FB', secure: false, type: socket.SppType.SPP_RFCOMM};
try {
    socket.sppListen('server1', sppOption, serverSocket);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
