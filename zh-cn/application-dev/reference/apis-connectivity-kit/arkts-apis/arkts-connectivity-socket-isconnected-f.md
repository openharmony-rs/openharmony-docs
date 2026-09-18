# isConnected

## 导入模块

```TypeScript
import { socket } from '@kit.ConnectivityKit';
```

## isConnected

```TypeScript
function isConnected(clientSocket: number): boolean
```

客户端和服务端均可使用，检查当前链路是否已连接。

**起始版本：** 22

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| clientSocket | number | 是 | 客户端套接字的ID。该值是调用[sppAccept](arkts-connectivity-socket-sppaccept-f.md)或[sppConnect](arkts-connectivity-socket-sppconnect-f.md)接口，通过其异步callback获取到的。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 套接字链路是否已连接，true表示已连接，false表示未连接。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 入参clientNumber由sppAccept或sppConnect接口获取。
let clientSocket = 1;
try {
    let result: boolean = socket.isConnected(clientSocket);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
