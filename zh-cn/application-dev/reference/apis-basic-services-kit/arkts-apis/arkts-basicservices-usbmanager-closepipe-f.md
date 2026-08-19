# closePipe

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';
```

## closePipe

```TypeScript
function closePipe(pipe: USBDevicePipe): int
```

关闭设备连接通道。 1. 调用[usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md)获取设备列表； 2. 调用[usbManager.requestRight](arkts-basicservices-usbmanager-requestright-f.md)获取设备请求权限； 3. 调用[usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md)得到devicepipe作为参数。

**起始版本：** 23

<!--Device-usbManager-function closePipe(pipe: USBDevicePipe): int--><!--Device-usbManager-function closePipe(pipe: USBDevicePipe): int-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | USBDevicePipe | 是 | 用于确定总线地址和设备地址，需要调用[connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md)获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 关闭设备连接通道成功返回0；关闭设备连接通道失败返回其他错误码如下： <br>- 22：服务异常。可能原因：1.USB服务未正常运行；2.设备连接通道状态异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  <br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

**示例**

```TypeScript
async function closePipe() {
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
  let ret: int = usbManager.closePipe(devicePipe);
  console.info(`closePipe = ${ret}`);
}
```

