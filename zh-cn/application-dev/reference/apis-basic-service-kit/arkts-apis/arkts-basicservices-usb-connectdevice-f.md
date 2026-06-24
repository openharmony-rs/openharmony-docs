# connectDevice

## connectDevice

```TypeScript
function connectDevice(device: USBDevice): Readonly<USBDevicePipe>
```

打开USB设备。

需要调用[usb.getDevices](arkts-basicservices-usb-getdevices-f.md#getDevices-1)获取设备信息以及device，再调用[usb.requestRight](arkts-basicservices-usb-requestright-f.md#requestRight-1)获取设备请求权限。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md#connectDevice-1)

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| device | USBDevice | 是 | USB设备信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Readonly&lt;USBDevicePipe&gt; | 指定的传输通道对象。 |

**示例：**

```TypeScript
let devicepipe= usb.connectDevice(device);
console.info(`devicepipe = ${devicepipe}`);

```

