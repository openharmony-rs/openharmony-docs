# connectDevice

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## connectDevice

```TypeScript
function connectDevice(device: USBDevice): Readonly<USBDevicePipe>
```

根据getDevices()返回的设备信息打开USB设备。如果USB服务异常，可能返回`undefined`，注意需要对接口返回值做判空处理。

1. 需要调用[usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md#getdevices-1)获取设备信息以及device;2. 调用[usbManager.requestRight](arkts-basicservices-usbmanager-requestright-f.md#requestright-1)请求使用该设备的权限。

**起始版本：** 9

<!--Device-usbManager-function connectDevice(device: USBDevice): Readonly<USBDevicePipe>--><!--Device-usbManager-function connectDevice(device: USBDevice): Readonly<USBDevicePipe>-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| device | [USBDevice](arkts-basicservices-usbmanager-usbdevice-i.md) | 是 | USB设备信息，用[usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md#getdevices-1)获取的busNum和devAddress确定设备，当前其他属性不做处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Readonly<USBDevicePipe> | 指定的传输通道对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:* <br>1.Mandatory parameters are left unspecified.* <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |
| [14400001](../../apis-basic-services-kit/errorcode-usb.md#14400001-连接usb设备被拒绝) | Access right denied. Call requestRight to get the USBDevicePipe access right first. |
| [14400004](../../apis-basic-services-kit/errorcode-usb.md#14400004-服务异常) |  |
| [14400012](../../apis-basic-services-kit/errorcode-usb.md#14400012-io错误) |  |

**示例：**

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
  let devicepipe: usbManager.USBDevicePipe = usbManager.connectDevice(device);
  if (devicepipe == undefined) {
    console.error(`connect device failed`);
    return;
  }
  console.info(`devicepipe = ${devicepipe}`);
  usbManager.closePipe(devicepipe);
}

```

