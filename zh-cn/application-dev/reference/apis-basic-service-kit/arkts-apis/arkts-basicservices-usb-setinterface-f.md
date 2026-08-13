# setInterface

## setInterface

```TypeScript
function setInterface(pipe: USBDevicePipe, iface: USBInterface): number
```

设置设备接口。 需要调用[usb.getDevices](arkts-basicservices-usb-getdevices-f.md#getDevices)获取设备列表以及interfaces；调用[usb.requestRight](arkts-basicservices-usb-requestright-f.md#requestRight)获取设备请求权限；调 用[usb.connectDevice](arkts-basicservices-usb-connectdevice-f.md#connectDevice)得到devicepipe作为参数；调用[usb.claimInterface](arkts-basicservices-usb-claiminterface-f.md#claimInterface)注册通信接 口。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [setInterface](arkts-basicservices-usbmanager-setinterface-f.md#setInterface)

<!--Device-usb-function setInterface(pipe: USBDevicePipe, iface: USBInterface): number--><!--Device-usb-function setInterface(pipe: USBDevicePipe, iface: USBInterface): number-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | USBDevicePipe | 是 | 用于确定总线号和设备地址。 |
| iface | USBInterface | 是 | 用于确定需要设置的接口。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 设置设备接口成功返回0；设置设备接口失败返回其他错误码。 |

## 示例

```TypeScript
let ret = usb.setInterface(devicepipe, interfaces);
console.info(`setInterface = ${ret}`);
```

