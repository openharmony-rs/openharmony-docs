# getFileDescriptor

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';
```

## getFileDescriptor

```TypeScript
function getFileDescriptor(pipe: USBDevicePipe): int
```

获取文件描述符。如果USB服务异常，可能返回错误码，注意需要对接口返回值做判空或错误码检查处理。

**起始版本：** 23

<!--Device-usbManager-function getFileDescriptor(pipe: USBDevicePipe): int--><!--Device-usbManager-function getFileDescriptor(pipe: USBDevicePipe): int-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | USBDevicePipe | 是 | 用于确定总线地址和设备地址，需要调用[connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md)获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回设备对应的文件描述符，失败返回其他错误码如下： <br>- 88080486：服务初始化中，请稍后重试。 <br>- 88080488：无设备访问权限，请先调用[requestRight]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  <br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

**示例**

```TypeScript
async function getFileDescriptor() {
  let devicesList: Array<usbManager.USBDevice> = usbManager.getDevices();
  if (!devicesList || devicesList.length == 0) {
    console.info(`device list is empty`);
    return;
  }

  let rightResult = await usbManager.requestRight(devicesList?.[0]?.name);
  if (!rightResult) {
    console.error(`request right failed`);
    return;
  }
  let devicePipe: usbManager.USBDevicePipe = usbManager.connectDevice(devicesList?.[0]);
  if (devicePipe == undefined) {
    console.error(`connect device failed`);
    return;
  }
  let ret: int = usbManager.getFileDescriptor(devicePipe);
  console.info(`getFileDescriptor = ${ret}`);
  let closeRet: int = usbManager.closePipe(devicePipe);
  console.info(`closePipe = ${closeRet}`);
}
```

