# setConfiguration

## setConfiguration

```TypeScript
function setConfiguration(pipe: USBDevicePipe, config: USBConfig): number
```

设置设备配置。 需要调用[usb.getDevices]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_获取设备信息以及config；调用[usb.requestRight]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_获取设备请求权限；调用 [usb.connectDevice]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_得到devicepipe作为参数。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [@ohos.usbManager:usbManager.setConfiguration](arkts-basicservices-usbmanager-setconfiguration-f.md#setconfiguration)

<!--Device-usb-function setConfiguration(pipe: USBDevicePipe, config: USBConfig): number--><!--Device-usb-function setConfiguration(pipe: USBDevicePipe, config: USBConfig): number-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 用于确定总线号和设备地址。 |
| config | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 用于确定需要设置的配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 设置设备配置成功返回0；设置设备配置失败返回其他错误码。 |

**示例：**

```TypeScript
let ret = usb.setConfiguration(devicepipe, config);
console.info(`setConfiguration = ${ret}`);
```

