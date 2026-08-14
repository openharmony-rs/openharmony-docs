# connectDevice

## connectDevice

```TypeScript
function connectDevice(device: USBDevice): Readonly<USBDevicePipe>
```

根据getDevices()返回的设备信息打开USB设备。如果USB服务异常，可能返回`undefined`，注意需要对接口返回值做判空处理。 1. 需要调用[usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md#getDevices)获取设备信息以及device; 2. 调用[usbManager.requestRight](arkts-basicservices-usbmanager-requestright-f.md#requestRight)请求使用该设备的权限。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-usbManager-function connectDevice(device: USBDevice): Readonly<USBDevicePipe>--><!--Device-usbManager-function connectDevice(device: USBDevice): Readonly<USBDevicePipe>-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| device | USBDevice | 是 | USB设备信息，用[usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md#getDevices)获取的busNum和devAddress确定设备，当前其他属性不做处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Readonly&lt;USBDevicePipe&gt; | 指定的传输通道对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  &lt;br&gt;1.Mandatory parameters are left unspecified.  &lt;br&gt;2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |
| [14400012](../../apis-basic-services-kit/errorcode-usb.md#14400012-io错误) | Transmission I/O error.<br>**适用版本：** 23+  **ArkTS模式：** 该错误码仅适用于ArkTS-Sta。 |
| [14400001](../../apis-basic-services-kit/errorcode-usb.md#14400001-usb设备访问权限被拒绝) | Access right denied. Call requestRight to get the USBDevicePipe access right first. |
| [14400004](../../apis-basic-services-kit/errorcode-usb.md#14400004-服务异常) | Service exception. Possible causes:  &lt;br&gt;1. No accessory is plugged in.<br>**适用版本：** 23+  **ArkTS模式：** 该错误码仅适用于ArkTS-Sta。 |

## 示例

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

