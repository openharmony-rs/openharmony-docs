# sppConnect

## 导入模块

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## sppConnect

```TypeScript
function sppConnect(device: string, option: SppOption, callback: AsyncCallback<number>): void
```

客户端向远端设备发起spp连接。

从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [sppConnect](arkts-connectivity-bluetoothmanager-sppconnect-f.md)

**需要权限：** ohos.permission.USE_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| device | string | 是 | 对端设备地址，例如："XX:XX:XX:XX:XX:XX"。 |
| option | [SppOption](arkts-connectivity-bluetooth-sppoption-i.md) | 是 | spp客户端连接配置参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 表示回调函数的入参，客户端socket的id。 |

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
let sppOption : bluetooth.SppOption = {uuid: '00001810-0000-1000-8000-00805F9B34FB', secure: false, type: 0};
bluetooth.sppConnect('XX:XX:XX:XX:XX:XX', sppOption, clientSocket);
```
