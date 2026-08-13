# closePipe

## closePipe

```TypeScript
function closePipe(pipe: USBDevicePipe): int
```

关闭设备消息控制通道。 1. 需要调用[usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md#getDevices)获取设备列表； 2. 调用[usbManager.requestRight](arkts-basicservices-usbmanager-requestright-f.md#requestRight)获取设备请求权限； 3. 调用[usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md#connectDevice)得到devicepipe作为参数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-usbManager-function closePipe(pipe: USBDevicePipe): int--><!--Device-usbManager-function closePipe(pipe: USBDevicePipe): int-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | USBDevicePipe | 是 | 用于确定USB设备消息控制通道，需要调用[usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md#connectDevice)获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 关闭设备消息控制通道成功返回0；关闭设备消息控制通道失败返回其他错误码如下： |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  &lt;br&gt;1.Mandatory parameters are left unspecified.  &lt;br&gt;2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

## 示例

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

