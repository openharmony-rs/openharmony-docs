# releaseInterface

## 导入模块

```TypeScript
import { usb } from '@kit.BasicServicesKit';
```

## releaseInterface

```TypeScript
function releaseInterface(pipe: USBDevicePipe, iface: USBInterface): number
```

释放注册过的通信接口。

需要调用[usb.claimInterface](arkts-basicservices-usb-claiminterface-f.md#claiminterface-1)先获取接口，才能使用此方法释放接口。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [releaseInterface](arkts-basicservices-usbmanager-releaseinterface-f.md#releaseinterface-1)

<!--Device-usb-function releaseInterface(pipe: USBDevicePipe, iface: USBInterface): number--><!--Device-usb-function releaseInterface(pipe: USBDevicePipe, iface: USBInterface): number-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | [USBDevicePipe](arkts-basicservices-usbmanager-usbdevicepipe-i.md) | 是 | 用于确定总线号和设备地址。 |
| iface | [USBInterface](arkts-basicservices-usb-usbinterface-i.md) | 是 | 用于确定需要释放接口的索引。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 释放接口成功返回0；释放接口失败返回其他错误码。 |

**示例：**

```TypeScript
let ret = usb.releaseInterface(devicepipe, interfaces);
console.info(`releaseInterface = ${ret}`);

```

