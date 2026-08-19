# connectDevice

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';
```

## connectDevice

```TypeScript
function connectDevice(device: USBDevice): Readonly<USBDevicePipe>
```

根据getDevices()返回的设备信息打开USB设备，调用成功后建立设备连接通道，可以进行后续的数据传输和设备控制操作。使用完后需要调用 [usbManager.closePipe](arkts-basicservices-usbmanager-closepipe-f.md)关闭设备连接通道。如果USB服务异常，会返回`undefined`，注意需要对接口返回值做判空处理。 1. 调用[usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md)获取设备信息以及USBDevice; 2. 调用[usbManager.requestRight](arkts-basicservices-usbmanager-requestright-f.md)请求使用该设备的权限。

**起始版本：** 23

<!--Device-usbManager-function connectDevice(device: USBDevice): Readonly<USBDevicePipe>--><!--Device-usbManager-function connectDevice(device: USBDevice): Readonly<USBDevicePipe>-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| device | USBDevice | 是 | USB设备信息，用[getDevices](arkts-basicservices-usbmanager-getdevices-f.md)获取的busNum和devAddress确定设备，当前其他属性（如 name、vendorId等）不参与设备匹配。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Readonly&lt;USBDevicePipe&gt; | USB设备连接通道对象，用于后续的数据传输和设备控制操作。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  <br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |
| [14400012](../errorcode-usb.md#14400012-io错误) |  |
| [14400001](../errorcode-usb.md#14400001-usb设备访问权限被拒绝) | Access right denied. Call requestRight to get the USBDevicePipe access right first. |
| [14400004](../errorcode-usb.md#14400004-服务异常) |  |

**示例**

```TypeScript
async function connectDevice() {
  let devicesList: Array<usbManager.USBDevice> = usbManager.getDevices();
  if (!devicesList || devicesList.length == 0) {
    console.info(`device list is empty`);
    return;
  }

  let device: usbManager.USBDevice = devicesList?.[0];
  let rightResult = await usbManager.requestRight(device.name);
  if (!rightResult) {
    console.error(`request right failed`);
    return;
  }
  let devicePipe: usbManager.USBDevicePipe = usbManager.connectDevice(device);
  if (devicePipe == undefined) {
    console.error(`connect device failed`);
    return;
  }
  console.info(`devicePipe = ${devicePipe}`);
  usbManager.closePipe(devicePipe);
}
```

