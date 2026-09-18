# getDeviceId

## 导入模块

```TypeScript
import { socket } from '@kit.ConnectivityKit';
```

## getDeviceId

```TypeScript
function getDeviceId(clientSocket: number): string
```

客户端和服务端均可使用，获取套接字连接中的对端设备蓝牙地址。若客户端使用，需在调用[socket.sppConnect](arkts-connectivity-socket-sppconnect-f.md)后，且连接成功后使用。若服务端使用，需在调用[socket.sppAccept](arkts-connectivity-socket-sppaccept-f.md)后，且连接成功后使用。

**起始版本：** 17

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| clientSocket | number | 是 | 客户端套接字的ID。该值是调用[socket.sppAccept](arkts-connectivity-socket-sppaccept-f.md)或[socket.sppConnect](arkts-connectivity-socket-sppconnect-f.md)接口后，通过其异步callback获取到的。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回对端设备地址。基于信息安全考虑，此处获取的设备地址为虚拟MAC地址。已配对的地址不会变更。若该设备重启蓝牙开关，重新获取到的虚拟地址会立即变更。若取消配对，蓝牙子系统会根据该地址是否仍被其他应用使用来决定变更时机：若其他应用正在使用该地址，则不会立即变更；当无应用使用时，地址将被回收并在下次获取时分配新的虚拟地址。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 服务端获取客户端设备地址。
let clientSocket = 1; // clientSocket是sppAccept回调中得到的，调用getDeviceId接口前需更新clientSocket。
try {
    let deviceAddr: string = socket.getDeviceId(clientSocket);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}

// 客户端获取服务端设备地址。
// clientSocket是sppConnect回调中得到的，调getDeviceId接口前需更新clientSocket。
try {
    let deviceAddr: string = socket.getDeviceId(clientSocket);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
