# setConfiguration

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';
```

## setConfiguration

```TypeScript
function setConfiguration(pipe: USBDevicePipe, config: USBConfiguration): int
```

设置设备配置。适用于多功能USB设备需要切换工作模式的场景，如打印机+扫描仪组合设备切换为打印模式或扫描模式、设备从低功耗配置切换到高功耗配置以启用全部功能等。调用成功后设备的配置将被切换为指定的配置，后续的数据传输和设备操作将基 于新配置进行。 > **说明：** > > 在调用该接口前需要调用[usbManager.claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md) claim通信接口。

**起始版本：** 23

<!--Device-usbManager-function setConfiguration(pipe: USBDevicePipe, config: USBConfiguration): int--><!--Device-usbManager-function setConfiguration(pipe: USBDevicePipe, config: USBConfiguration): int-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | USBDevicePipe | 是 | 用于确定总线地址和设备地址，需要调用[connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md)获取。 |
| config | [USBConfiguration](arkts-basicservices-usbmanager-usbconfiguration-i.md) | 是 | 用于确定需要设置的配置，需要调用[getDevices](arkts-basicservices-usbmanager-getdevices-f.md)获取设备信息并通过id确定唯一配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回设置设备配置操作的结果。设置设备配置成功返回0；设置设备配置失败返回其他错误码如下： <br>- 88080389：服务未启动，可能原因：1.无设备插入；2.服务异常退出。 <br>- 88080486：服务初始化中，请稍后重试。 <br>- 88080488：无设备访问权限，请先调用[requestRight]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  <br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

**示例**

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
  let devicePipe: usbManager.USBDevicePipe = usbManager.connectDevice(device);
  if (devicePipe == undefined) {
    console.error(`connect device failed`);
    return;
  }
  let config: usbManager.USBConfiguration = device.configs?.[0];
  let ret: int = usbManager.setConfiguration(devicePipe, config);
  console.info(`setConfiguration = ${ret}`);
  usbManager.closePipe(devicePipe);
}
```

