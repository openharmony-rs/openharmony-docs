# claimInterface

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';
```

## claimInterface

```TypeScript
function claimInterface(pipe: USBDevicePipe, iface: USBInterface, force?: boolean): int
```

声明对USB设备某个接口的控制权。调用成功后应用获得该接口的独占控制权可以进行数据传输等操作，其他程序无法访问该接口。使用完后需调用 [releaseInterface](arkts-basicservices-usbmanager-releaseinterface-f.md)释放该接口的控制权。 **使用场景**：在需要进行USB数据传输时，需要先声明接口控制权以独占访问该接口。例如，在USB存储设备读写、USB摄像头数据采集、USB串口通信等场景中，都需要先声明接口控制权。 > **说明：** > > 在USB编程中，claim interface是一个常见操作，指的是应用请求操作系统将某个USB接口从内核驱动中释放并交由用户空间程序控制。 > 下面用到的claim通信接口都表示claim interface操作。

**起始版本：** 23

<!--Device-usbManager-function claimInterface(pipe: USBDevicePipe, iface: USBInterface, force?: boolean): int--><!--Device-usbManager-function claimInterface(pipe: USBDevicePipe, iface: USBInterface, force?: boolean): int-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | USBDevicePipe | 是 | 用于确定总线地址和设备地址，需要调用[connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md)获取。 |
| iface | USBInterface | 是 | 用于确定需要获取控制的接口对象，需要调用[getDevices](arkts-basicservices-usbmanager-getdevices-f.md)获取设备信息并通过id确定唯一接口。 |
| force | boolean | 否 | 可选参数，是否强制获取。默认值为false，表示不强制获取；设置为true时，将强制从内核驱动或其他程序中释放该接口的控制权并交由用户空间程序控制。如果接口已被其他程序占 用，使用true可强制获取但可能导致该程序功能异常；如果接口未被占用，建议使用false以避免不必要的强制操作。用户按需选择。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | claim通信接口成功返回0；claim通信接口失败返回其他错误码如下： <br>- 88080389：服务未启动，可能原因：1.无设备插入；2.服务异常退出。 <br>- 88080486：服务初始化中，请稍后重试。 <br>- 88080488：无设备访问权限，请先调用[requestRight]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  <br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

**示例**

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

