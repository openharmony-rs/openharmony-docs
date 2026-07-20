# claimInterface

## 导入模块

```TypeScript
import { usb } from '@kit.BasicServicesKit';
```

<a id="claiminterface"></a>
## claimInterface

```TypeScript
function claimInterface(pipe: USBDevicePipe, iface: USBInterface, force?: boolean): number
```

注册通信接口。

需要调用[usb.getDevices](arkts-basicservices-usb-getdevices-f.md#getdevices-1)获取设备信息以及interfaces；调用[usb.requestRight](arkts-basicservices-usb-requestright-f.md#requestright-1)获取设备请求权限；调用[usb.connectDevice](arkts-basicservices-usb-connectdevice-f.md#connectdevice-1)接口得到devicepipe作为参数。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md#claiminterface-1)

<!--Device-usb-function claimInterface(pipe: USBDevicePipe, iface: USBInterface, force?: boolean): number--><!--Device-usb-function claimInterface(pipe: USBDevicePipe, iface: USBInterface, force?: boolean): number-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | [USBDevicePipe](arkts-basicservices-usbmanager-usbdevicepipe-i.md) | 是 | 用于确定总线号和设备地址。 |
| iface | [USBInterface](arkts-basicservices-usb-usbinterface-i.md) | 是 | 用于确定需要获取接口的索引。 |
| force | boolean | 否 | 可选参数，是否强制获取。默认值为false?，表示不强制获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 注册通信接口成功返回0；注册通信接口失败返回其他错误码。 |

**示例：**

```TypeScript
let ret = usb.claimInterface(devicepipe, interfaces);
console.info(`claimInterface = ${ret}`);

```

