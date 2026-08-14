# setInterface

## setInterface

```TypeScript
function setInterface(pipe: USBDevicePipe, iface: USBInterface): int
```

设置设备接口。 > **说明：** > > 一个USB接口可能存在多重选择模式，支持动态切换。使用的场景：数据传输时，通过该接口可重新设置端点，使端点与传输类型匹配。 > > 在调用该接口前需要通过 > [usbManager.claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md#claimInterface) > claim通信接口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-usbManager-function setInterface(pipe: USBDevicePipe, iface: USBInterface): int--><!--Device-usbManager-function setInterface(pipe: USBDevicePipe, iface: USBInterface): int-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | USBDevicePipe | 是 | 用于确定总线号和设备地址，需要调用[usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md#connectDevice)获取。 |
| iface | USBInterface | 是 | 用于确定需要设置的接口，需要调用[usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md#getDevices)获取设备信息并通过id和alternateSetting确定唯一接口。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 设置设备接口成功返回0；设置设备接口失败返回其他错误码如下： |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  &lt;br&gt;1.Mandatory parameters are left unspecified.  &lt;br&gt;2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

## 示例

```TypeScript
async function setInterface() {
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
  let interfaces: usbManager.USBInterface = device.configs?.[0]?.interfaces?.[0];
  let ret: int = usbManager.claimInterface(devicePipe, interfaces);
  if (ret !== 0) {
    console.error(`claim interface failed`);
    return;
  }
  ret = usbManager.setInterface(devicePipe, interfaces);
  console.info(`setInterface = ${ret}`);
  ret = usbManager.releaseInterface(devicePipe, interfaces);
  console.info(`releaseInterface = ${ret}`);
  usbManager.closePipe(devicePipe);
}
```

