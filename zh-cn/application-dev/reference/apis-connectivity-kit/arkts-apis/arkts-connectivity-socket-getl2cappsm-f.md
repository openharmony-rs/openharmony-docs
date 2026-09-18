# getL2capPsm

## 导入模块

```TypeScript
import { socket } from '@kit.ConnectivityKit';
```

## getL2capPsm

```TypeScript
function getL2capPsm(serverSocket: number): number
```

获取服务端L2CAP链路类型套接字的协议/服务多路复用器值（Protocol/Service Multiplexer, PSM），该值用于标识特定的服务数据传输通道。

需要在服务端调用完[socket.sppListen](arkts-connectivity-socket-spplisten-f.md)后调用该接口，且传入的链路类型[SppType](arkts-connectivity-socket-spptype-e.md)需是SPP_L2CAP或SPP_L2CAP_BLE。

**起始版本：** 20

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| serverSocket | number | 是 | 服务端套接字的ID。该值是调用[socket.sppListen](arkts-connectivity-socket-spplisten-f.md)接口后，通过其异步callback获取到的。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回L2CAP链路类型套接字的psm值。[SppType](arkts-connectivity-socket-spptype-e.md)设置为SPP_L2CAP_BLE时，返回值的有效值范围为[0x01, 0xFF]。[SppType](arkts-connectivity-socket-spptype-e.md)设置为SPP_L2CAP时，返回值的有效值范围为[0x0000, 0xFFFF]。服务端通道建立异常或[SppType](arkts-connectivity-socket-spptype-e.md)非L2CAP链路类型时，返回-1。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 服务端获取客户端设备地址。
let serverNumber = 1; // 此处serverNumber需赋值为调用sppListen接口后，回调中得到的serverNumber。
try {
    let l2capPsm: number = socket.getL2capPsm(serverNumber);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
