# setInterface

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';
```

## setInterface

```TypeScript
function setInterface(pipe: USBDevicePipe, iface: USBInterface): int
```

设置设备接口。调用成功后接口将被切换到指定的备用设置，端点配置将随之改变以匹配传输类型要求。 > **说明：** > > 一个USB接口可能存在多重选择模式，支持动态切换。使用的场景：数据传输时，通过该接口可重新设置端点，使端点与传输类型匹配。 > > 在调用该接口前需要通过[usbManager.claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md) claim通信接口。

**起始版本：** 23

<!--Device-usbManager-function setInterface(pipe: USBDevicePipe, iface: USBInterface): int--><!--Device-usbManager-function setInterface(pipe: USBDevicePipe, iface: USBInterface): int-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | USBDevicePipe | 是 | 用于确定总线地址和设备地址，需要调用[connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md)获取。 |
| iface | USBInterface | 是 | 用于确定需要设置的接口，需要调用[getDevices](arkts-basicservices-usbmanager-getdevices-f.md)获取设备信息，通过接口的id和 alternateSetting共同确定唯一接口，其中id为接口的唯一标识符，alternateSetting用于在同一接口的多个可选模式间切换，为0时表示不支持可选模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回设置设备接口操作的结果。设置设备接口成功返回0；设置设备接口失败返回其他错误码如下： <br>- 88080389：服务未启动，可能原因：1.无设备插入；2.服务异常退出。 <br>- 88080486：服务初始化中，请稍后重试。 <br>- 88080488：无设备访问权限，请先调用[requestRight]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  <br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

**示例**

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

