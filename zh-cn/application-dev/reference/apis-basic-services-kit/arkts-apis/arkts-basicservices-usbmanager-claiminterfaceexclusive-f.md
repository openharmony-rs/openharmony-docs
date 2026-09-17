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

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

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
