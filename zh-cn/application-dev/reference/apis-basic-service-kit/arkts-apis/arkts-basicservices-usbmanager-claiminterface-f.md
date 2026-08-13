# claimInterface

## claimInterface

```TypeScript
function claimInterface(pipe: USBDevicePipe, iface: USBInterface, force?: boolean): int
```

声明对USB设备某个接口的控制权。 > **说明：** > > 在USB编程中，claim interface是一个常见操作，指的是应用程序请求操作系统将某个USB接口从内核驱动中释放并交由用户空间程序控制。&lt;br&gt; > > 下面用到的claim通信接口都表示claim interface操作。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-usbManager-function claimInterface(pipe: USBDevicePipe, iface: USBInterface, force?: boolean): int--><!--Device-usbManager-function claimInterface(pipe: USBDevicePipe, iface: USBInterface, force?: boolean): int-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | USBDevicePipe | 是 | 用于确定总线号和设备地址，需要调用[usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md#connectDevice)获取。 |
| iface | USBInterface | 是 | 用于确定需要获取接口的索引，需要调用[usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md#getDevices)获取设备信息并通过id确定唯一接口。 |
| force | boolean | 否 | 可选参数，是否强制获取。默认值为false?，表示不强制获取，用户按需选择。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | claim通信接口成功返回0；claim通信接口失败返回其他错误码如下： |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  &lt;br&gt;1.Mandatory parameters are left unspecified.  &lt;br&gt;2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

## 示例

```TypeScript
async function claimInterface() {
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
  console.info(`claimInterface = ${ret}`);
  ret = usbManager.releaseInterface(devicePipe, interfaces);
  console.info(`releaseInterface = ${ret}`);
  usbManager.closePipe(devicePipe);
}
```

