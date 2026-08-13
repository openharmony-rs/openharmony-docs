# resetUsbDevice

## resetUsbDevice

```TypeScript
function resetUsbDevice(pipe: USBDevicePipe): boolean
```

重置USB外设。 > **说明：** > > 本接口调用后会重置此前设置的配置和替换接口，请在调用之前确认相关业务已结束。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-usbManager-function resetUsbDevice(pipe: USBDevicePipe): boolean--><!--Device-usbManager-function resetUsbDevice(pipe: USBDevicePipe): boolean-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | USBDevicePipe | 是 | 用于确定总线号和设备地址，需要调用[usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md#connectDevice)获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示重置设备成功，false表示重置设备失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14400010](../../apis-basic-services-kit/errorcode-usb.md#14400010-无法识别的错误) | Other USB error. Possible causes:  &lt;br&gt;1.Unrecognized discard error code. |
| [14400008](../../apis-basic-services-kit/errorcode-usb.md#14400008-没有设备连接已断开) | No such device(it may have been disconnected) |
| [14400013](../../apis-basic-services-kit/errorcode-usb.md#14400013-参数合法性检查失败) | The USBDevicePipe validity check failed. Possible causes:  &lt;br&gt;1.The input parameters fail the validation check.  &lt;br&gt;2.The call chain used to obtain the input parameters is not reasonable. |
| [14400001](../../apis-basic-services-kit/errorcode-usb.md#14400001-usb设备访问权限被拒绝) | Access right denied. Call requestRight to get the USBDevicePipe access right first. |
| [14400004](../../apis-basic-services-kit/errorcode-usb.md#14400004-服务异常) | Service exception. Possible causes: 1. No accessory is plugged in. |

## 示例

```TypeScript
async function resetUsbDevice() {
  let devicesList: Array<usbManager.USBDevice> = usbManager.getDevices();
  if (!devicesList || devicesList.length == 0) {
    console.error(`device list is empty`);
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
  try {
    let ret: boolean = usbManager.resetUsbDevice(devicePipe);
    console.info(`resetUsbDevice  = ${ret}`);
  } catch (err) {
    console.error(`Failed to reset USB device. Code: ${err.code}, message: ${err.message}`);
  }
  usbManager.closePipe(devicePipe);
}
```

