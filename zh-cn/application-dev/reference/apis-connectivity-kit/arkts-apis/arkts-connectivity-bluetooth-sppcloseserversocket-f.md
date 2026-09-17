# sppCloseServerSocket

## 导入模块

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## sppCloseServerSocket

```TypeScript
function sppCloseServerSocket(socket: number): void
```

关闭服务端监听Socket，入参socket由sppListen接口返回。

从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [sppCloseServerSocket](arkts-connectivity-bluetoothmanager-sppcloseserversocket-f.md)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| socket | number | 是 | 服务端监听socket的id。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
let serverNumber = -1;
function serverSocket(code : BusinessError, number : number) {
  console.info(`bluetooth error code: ${code.code}`);
  if (code.code == 0) {
    console.info(`bluetooth serverSocket Number: ${number}`);
    serverNumber = number;
  }
}
bluetooth.sppCloseServerSocket(serverNumber);
```
