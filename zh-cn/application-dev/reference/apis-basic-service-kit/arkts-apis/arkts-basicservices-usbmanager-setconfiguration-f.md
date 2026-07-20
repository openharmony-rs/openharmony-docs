# setConfiguration

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

<a id="setconfiguration"></a>
## setConfiguration

```TypeScript
function setConfiguration(pipe: USBDevicePipe, config: USBConfiguration): number
```

设置设备配置。

**起始版本：** 9

<!--Device-usbManager-function setConfiguration(pipe: USBDevicePipe, config: USBConfiguration): int--><!--Device-usbManager-function setConfiguration(pipe: USBDevicePipe, config: USBConfiguration): int-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | [USBDevicePipe](arkts-basicservices-usbmanager-usbdevicepipe-i.md) | 是 | 用于确定总线号和设备地址，需要调用[usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md#connectdevice-1)获取。 |
| config | [USBConfiguration](arkts-basicservices-usbmanager-usbconfiguration-i.md) | 是 | 用于确定需要设置的配置，需要调用[usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md#getdevices-1)获取设备信息并通过id用于确定唯一设置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 设置设备配置成功返回0；设置设备配置失败返回其他错误码如下：* - 88080389：服务未启动，可能原因：1.无设备插入；2.服务异常退出。* - 88080486：服务初始化中，请稍后重试。* - 88080488：无设备访问权限，请先调用[usbManager.requestRight](arkts-basicservices-usbmanager-requestright-f.md#requestright-1)接口申请授权。* - -1：驱动异常。* - -17：I/O失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:* <br>1.Mandatory parameters are left unspecified.* <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

**示例：**

```TypeScript
async function setConfiguration() {
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
  let config: usbManager.USBConfiguration = device.configs?.[0];
  let ret: number = usbManager.setConfiguration(devicepipe, config);
  console.info(`setConfiguration = ${ret}`);
  usbManager.closePipe(devicepipe);
}

```

