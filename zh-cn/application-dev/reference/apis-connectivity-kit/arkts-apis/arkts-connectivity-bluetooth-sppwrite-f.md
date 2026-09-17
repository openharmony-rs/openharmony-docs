# sppWrite

## 导入模块

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## sppWrite

```TypeScript
function sppWrite(clientSocket: number, data: ArrayBuffer): boolean
```

通过socket向远端发送数据，入参clientSocket由sppAccept或sppConnect接口获取 。

从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [sppWrite](arkts-connectivity-bluetoothmanager-sppwrite-f.md)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| clientSocket | number | 是 | 客户端socket的id。 |
| data | ArrayBuffer | 是 | 写入的数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 写数据操作，成功返回true，否则返回false。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
let clientNumber = -1;
function clientSocket(code : BusinessError, number : number) {
  if (code == null || code.code != 0) {
    return;
  }
  console.info(`bluetooth serverSocket Number: ${number}`);
  // 获取的clientNumber用作客户端后续读/写操作socket的id。
  clientNumber = number;
}
let arrayBuffer = new ArrayBuffer(8);
let data = new Uint8Array(arrayBuffer);
data[0] = 123;
let ret : boolean = bluetooth.sppWrite(clientNumber, arrayBuffer);
if (ret) {
  console.info('spp write successfully');
} else {
  console.error('spp write failed');
}
```
