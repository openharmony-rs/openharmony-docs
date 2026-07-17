# setConfiguration

## 导入模块

```TypeScript
import { usb } from '@kit.BasicServicesKit';
```

## setConfiguration

```TypeScript
function setConfiguration(pipe: USBDevicePipe, config: USBConfig): number
```

设置设备配置。

需要调用[usb.getDevices](arkts-basicservices-usb-getdevices-f.md#getdevices-1)获取设备信息以及config；调用[usb.requestRight](arkts-basicservices-usb-requestright-f.md#requestright-1)获取设备请求权限；调用[usb.connectDevice](arkts-basicservices-usb-connectdevice-f.md#connectdevice-1)得到devicepipe作为参数。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [setConfiguration](arkts-basicservices-usbmanager-setconfiguration-f.md#setconfiguration-1)

<!--Device-usb-function setConfiguration(pipe: USBDevicePipe, config: USBConfig): number--><!--Device-usb-function setConfiguration(pipe: USBDevicePipe, config: USBConfig): number-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | [USBDevicePipe](arkts-basicservices-usbmanager-usbdevicepipe-i.md) | 是 | 用于确定总线号和设备地址。 |
| config | [USBConfig](arkts-basicservices-usb-usbconfig-i.md) | 是 | 用于确定需要设置的配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 设置设备配置成功返回0；设置设备配置失败返回其他错误码。 |

**示例：**

```TypeScript
let ret = usb.setConfiguration(devicepipe, config);
console.info(`setConfiguration = ${ret}`);

```

