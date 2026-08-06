# releaseInterface

## releaseInterface

```TypeScript
function releaseInterface(pipe: USBDevicePipe, iface: USBInterface): number
```

释放注册过的通信接口。 需要调用[usb.claimInterface]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_先获取接口，才能使用此方法释放接口。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [@ohos.usbManager:usbManager.releaseInterface](arkts-basicservices-usbmanager-releaseinterface-f.md#releaseinterface)

<!--Device-usb-function releaseInterface(pipe: USBDevicePipe, iface: USBInterface): number--><!--Device-usb-function releaseInterface(pipe: USBDevicePipe, iface: USBInterface): number-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 用于确定总线号和设备地址。 |
| iface | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 用于确定需要释放接口的索引。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 释放接口成功返回0；释放接口失败返回其他错误码。 |

**示例：**

```TypeScript
let ret = usb.releaseInterface(devicepipe, interfaces);
console.info(`releaseInterface = ${ret}`);
```

