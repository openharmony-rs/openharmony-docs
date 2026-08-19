# resetUsbDevice

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';
```

## resetUsbDevice

```TypeScript
function resetUsbDevice(pipe: USBDevicePipe): boolean
```

重置USB设备。适用于USB设备出现通信异常需要恢复的场景，如设备固件升级后需要重新初始化、设备状态异常需要恢复、调试过程中需要重置设备状态等。调用成功后设备将被重置为初始状态，此前设置的配置和接口设置将被清除，设备需要重新初始 化。 > **说明：** > > 本接口调用后会重置此前设置的配置和接口设置，请在调用之前确认相关业务已结束。 1. 调用[usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md)获取设备列表。 2. 调用[usbManager.requestRight](arkts-basicservices-usbmanager-requestright-f.md)获取设备请求权限。 3. 调用[usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md)得到devicepipe作为参数。

**起始版本：** 23

<!--Device-usbManager-function resetUsbDevice(pipe: USBDevicePipe): boolean--><!--Device-usbManager-function resetUsbDevice(pipe: USBDevicePipe): boolean-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | USBDevicePipe | 是 | 用于确定总线地址和设备地址，需要调用[connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md)获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示重置设备成功，false表示重置设备失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14400010](../errorcode-usb.md#14400010-无法识别的错误) | Other USB error. Possible causes:  <br>1.Unrecognized discard error code. |
| [14400008](../errorcode-usb.md#14400008-没有设备连接已断开) | No such device(it may have been disconnected). |
| [14400013](../errorcode-usb.md#14400013-参数合法性检查失败) | The USBDevicePipe validity check failed. Possible causes:  <br>1.The input parameters fail the validation check.  <br>2.The call chain used to obtain the input parameters is not reasonable. |
| [14400001](../errorcode-usb.md#14400001-usb设备访问权限被拒绝) | Access right denied. Call requestRight to get the USBDevicePipe access right first. |
| [14400004](../errorcode-usb.md#14400004-服务异常) |  |

**示例**

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

