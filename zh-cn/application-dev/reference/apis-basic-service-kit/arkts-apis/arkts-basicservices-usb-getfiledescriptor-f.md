# getFileDescriptor

## getFileDescriptor

```TypeScript
function getFileDescriptor(pipe: USBDevicePipe): number
```

获取文件描述符。

需要调用[usb.getDevices](arkts-basicservices-usb-getdevices-f.md#getDevices-1)获取设备列表；调用[usb.requestRight](arkts-basicservices-usb-requestright-f.md#requestRight-1)获取设备请求权限；调用
[usb.connectDevice](arkts-basicservices-usb-connectdevice-f.md#connectDevice-1)接口得到devicepipe作为参数。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getFileDescriptor](arkts-basicservices-usbmanager-getfiledescriptor-f.md#getFileDescriptor-1)

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | USBDevicePipe | 是 | 用于确定总线号和设备地址。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回设备对应的文件描述符；失败返回-1。 |

**示例：**

```TypeScript
let ret = usb.getFileDescriptor(devicepipe);

```

