# closePipe

## closePipe

```TypeScript
function closePipe(pipe: USBDevicePipe): number
```

关闭设备消息控制通道。 需要调用[usb.getDevices]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_获取设备列表；调用[usb.requestRight]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_获取设备请求权限；调用 [usb.connectDevice]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_得到devicepipe作为参数。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [@ohos.usbManager:usbManager.closePipe](arkts-basicservices-usbmanager-closepipe-f.md#closepipe)

<!--Device-usb-function closePipe(pipe: USBDevicePipe): number--><!--Device-usb-function closePipe(pipe: USBDevicePipe): number-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 用于确定USB设备消息控制通道。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 关闭设备消息控制通道成功返回0；关闭设备消息控制通道失败返回其他错误码。 |

**示例：**

```TypeScript
let ret = usb.closePipe(devicepipe);
console.info(`closePipe = ${ret}`);
```

