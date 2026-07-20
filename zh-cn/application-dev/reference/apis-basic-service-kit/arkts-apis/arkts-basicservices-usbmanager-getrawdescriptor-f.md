# getRawDescriptor

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

<a id="getrawdescriptor"></a>
## getRawDescriptor

```TypeScript
function getRawDescriptor(pipe: USBDevicePipe): Uint8Array
```

获取原始的USB描述符。如果USB服务异常，可能返回`undefined`，注意需要对接口返回值做判空处理。

**起始版本：** 9

<!--Device-usbManager-function getRawDescriptor(pipe: USBDevicePipe): Uint8Array--><!--Device-usbManager-function getRawDescriptor(pipe: USBDevicePipe): Uint8Array-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | [USBDevicePipe](arkts-basicservices-usbmanager-usbdevicepipe-i.md) | 是 | 用于确定总线号和设备地址，需要调用[usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md#connectdevice-1)获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 返回获取的原始数据；失败返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:* <br>1.Mandatory parameters are left unspecified.* <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |
| [14400001](../../apis-basic-services-kit/errorcode-usb.md#14400001-连接usb设备被拒绝) |  |
| [14400004](../../apis-basic-services-kit/errorcode-usb.md#14400004-服务异常) |  |

**示例：**

```TypeScript
async function getRawDescriptor() {
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
  let devicepipe: usbManager.USBDevicePipe = usbManager.connectDevice(devicesList?.[0]);
  if (devicepipe == undefined) {
    console.error(`connect device failed`);
    return;
  }
  usbManager.getRawDescriptor(devicepipe);
  usbManager.closePipe(devicepipe);
}

```

