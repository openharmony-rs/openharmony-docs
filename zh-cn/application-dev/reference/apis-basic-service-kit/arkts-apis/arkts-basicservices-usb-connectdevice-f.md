# connectDevice

## connectDevice

```TypeScript
function connectDevice(device: USBDevice): Readonly<USBDevicePipe>
```

打开USB设备。 需要调用[usb.getDevices]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_获取设备信息以及device，再调用[usb.requestRight]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_获取设备请求权限。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [@ohos.usbManager:usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md#connectdevice)

<!--Device-usb-function connectDevice(device: USBDevice): Readonly<USBDevicePipe>--><!--Device-usb-function connectDevice(device: USBDevice): Readonly<USBDevicePipe>-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| device | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | USB设备信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Readonly&lt;USBDevicePipe&gt; | 指定的传输通道对象。 |

**示例：**

```TypeScript
let devicepipe= usb.connectDevice(device);
console.info(`devicepipe = ${devicepipe}`);
```

