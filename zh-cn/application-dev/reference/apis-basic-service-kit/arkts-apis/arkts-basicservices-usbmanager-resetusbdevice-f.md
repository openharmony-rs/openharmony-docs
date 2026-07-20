# resetUsbDevice

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

<a id="resetusbdevice"></a>
## resetUsbDevice

```TypeScript
function resetUsbDevice(pipe: USBDevicePipe): boolean
```

重置USB外设。

> **说明：**  
>  
> 本接口调用后会重置此前设置的配置和替换接口，请在调用之前确认相关业务已结束。

**起始版本：** 20

<!--Device-usbManager-function resetUsbDevice(pipe: USBDevicePipe): boolean--><!--Device-usbManager-function resetUsbDevice(pipe: USBDevicePipe): boolean-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | [USBDevicePipe](arkts-basicservices-usbmanager-usbdevicepipe-i.md) | 是 | 用于确定总线号和设备地址，需要调用[usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md#connectdevice-1)获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示重置设备成功，false表示重置设备失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14400001](../../apis-basic-services-kit/errorcode-usb.md#14400001-连接usb设备被拒绝) | Access right denied. Call requestRight to get the USBDevicePipe access right first. |
| [14400004](../../apis-basic-services-kit/errorcode-usb.md#14400004-服务异常) | Service exception. Possible causes: 1. No accessory is plugged in. |
| [14400008](../../apis-basic-services-kit/errorcode-usb.md#14400008-没有设备连接已断开) | No such device(it may have been disconnected) |
| [14400010](../../apis-basic-services-kit/errorcode-usb.md#14400010-无法识别的错误) | Other USB error. Possible causes:* <br>1.Unrecognized discard error code. |
| [14400013](../../apis-basic-services-kit/errorcode-usb.md#14400013-参数合法性检查失败) | The USBDevicePipe validity check failed. Possible causes:* <br>1.The input parameters fail the validation check.* <br>2.The call chain used to obtain the input parameters is not reasonable. |

**示例：**

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
  let devicepipe: usbManager.USBDevicePipe = usbManager.connectDevice(devicesList?.[0]);
  if (devicepipe == undefined) {
    console.error(`connect device failed`);
    return;
  }
  try {
    let ret: boolean = usbManager.resetUsbDevice(devicepipe);
    console.info(`resetUsbDevice  = ${ret}`);
  } catch (err: BusinessError) {
    console.error(`Failed to reset USB device. Code: ${err.code}, message: ${err.message}`);
  }
  usbManager.closePipe(devicepipe);
}

```

