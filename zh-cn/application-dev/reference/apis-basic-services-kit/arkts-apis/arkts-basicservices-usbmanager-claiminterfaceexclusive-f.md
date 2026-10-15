# claimInterfaceExclusive

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## claimInterfaceExclusive

```TypeScript
function claimInterfaceExclusive(pipe: USBDevicePipe, iface: USBInterface, force?: boolean,
    onConflict?: Callback<InterfaceConflictInfo>): void
```

独占方式声明USB设备接口。本接口在调用时检查指定的USB接口是否已被其他进程占用，避免声明时发生冲突。设置**force**为**true**时，操作系统会先从内核驱动程序中释放该接口，再将控制权授予调用方应用。独占声明成功后，其他进程仍可通过[usbManager.claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md)声明同一接口；可使用**onConflict**回调接收此类冲突通知。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-usbManager-function claimInterfaceExclusive(pipe: USBDevicePipe, iface: USBInterface, force?: boolean,    onConflict?: Callback<InterfaceConflictInfo>): void--><!--Device-usbManager-function claimInterfaceExclusive(pipe: USBDevicePipe, iface: USBInterface, force?: boolean,    onConflict?: Callback<InterfaceConflictInfo>): void-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | [USBDevicePipe](arkts-basicservices-usbmanager-usbdevicepipe-i.md) | 是 | 总线地址和设备地址，通过调用[usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md)获取。 |
| iface | [USBInterface](arkts-basicservices-usbmanager-usbinterface-i.md) | 是 | 目标USB接口的索引。可以使用[usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md)获取设备信息，并根据ID识别USB接口。 |
| force | boolean | 否 | 是否强制声明USB接口。默认值为**false**，表示不强制声明USB接口。可以根据需要设置该值。<br>默认值：false。 |
| onConflict | [Callback](arkts-basicservices-base-callback-i.md)&lt;[InterfaceConflictInfo](arkts-basicservices-usbmanager-interfaceconflictinfo-i.md)&gt; | 否 | 回调函数，返回独占声明成功后其他进程通过非互斥的[usbManager.claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md)接口声明同一USB接口时的冲突信息。如果不指定此参数，则发生此类冲突时不发送通知。<br>默认值：不触发回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14400001](../errorcode-usb.md#14400001-usb设备访问权限被拒绝) | Permission denied. |
| [14400004](../errorcode-usb.md#14400004-服务异常) | Service exception. |
| [14400007](../errorcode-usb.md#14400007-资源繁忙) | Resource busy. Possible cause: The interface is claimed by another program or driver. |
| [14400010](../errorcode-usb.md#14400010-无法识别的错误) | USB driver error. Possible causes: <br>1. The device is not connected using [usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md). <br>2. The USB device state is abnormal. |

**示例**

```TypeScript
async function claimInterfaceExclusive() {
  // 获取USB设备列表
  let devicesList: Array<usbManager.USBDevice>;
  try {
    devicesList = usbManager.getDevices();
  } catch (err) {
    console.error(`getDevices failed, err=${JSON.stringify(err)}`);
    return;
  }
  if (!devicesList || devicesList.length == 0) {
    console.info(`device list is empty`);
    return;
  }

  let device: usbManager.USBDevice = devicesList?.[0];
  // 申请设备访问权限
  let rightResult: boolean;
  try {
    rightResult = await usbManager.requestRight(device.name);
  } catch (err) {
    console.error(`requestRight failed, err=${JSON.stringify(err)}`);
    return;
  }
  if (!rightResult) {
    console.error(`request right failed`);
    return;
  }
  // 建立设备连接
  let devicePipe: usbManager.USBDevicePipe;
  try {
    devicePipe = usbManager.connectDevice(device);
  } catch (err) {
    console.error(`connectDevice failed, err=${JSON.stringify(err)}`);
    return;
  }
  if (devicePipe == undefined) {
    console.error(`connect device failed`);
    return;
  }
  let interfaces: usbManager.USBInterface = device.configs?.[0]?.interfaces?.[0];
  // 独占声明接口，并注册冲突回调
  try {
    usbManager.claimInterfaceExclusive(devicePipe, interfaces, false, (conflictInfo: usbManager.InterfaceConflictInfo) => {
      console.info(`interface conflict: busNum=${conflictInfo.busNum}, devAddr=${conflictInfo.devAddr}, interfaceId=${conflictInfo.interfaceId}`);
    });
  } catch (err) {
    console.error(`claimInterfaceExclusive failed, err=${JSON.stringify(err)}`);
  }
  console.info(`claimInterfaceExclusive success`);
  // 释放接口并关闭连接
  try {
    let ret: number = usbManager.releaseInterface(devicePipe, interfaces);
    console.info(`releaseInterface = ${ret}`);
  } catch (err) {
    console.error(`releaseInterface failed, err=${JSON.stringify(err)}`);
  }
  try {
    usbManager.closePipe(devicePipe);
  } catch (err) {
    console.error(`closePipe failed, err=${JSON.stringify(err)}`);
  }
}
```
