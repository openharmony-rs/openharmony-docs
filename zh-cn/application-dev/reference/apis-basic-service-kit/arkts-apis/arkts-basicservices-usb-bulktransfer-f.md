# bulkTransfer

## 导入模块

```TypeScript
import { usb } from '@kit.BasicServicesKit';
```

## bulkTransfer

```TypeScript
function bulkTransfer(
    pipe: USBDevicePipe,
    endpoint: USBEndpoint,
    buffer: Uint8Array,
    timeout?: number
  ): Promise<number>
```

批量传输。

需要调用[usb.getDevices](arkts-basicservices-usb-getdevices-f.md#getdevices)获取设备信息列表以及endpoint；再调用[usb.requestRight](arkts-basicservices-usb-requestright-f.md#requestright)获取设备请求权限；然后调用[usb.connectDevice](arkts-basicservices-usb-connectdevice-f.md#connectdevice)接口得到返回数据devicepipe之后，再次获取接口[usb.claimInterface](arkts-basicservices-usb-claiminterface-f.md#claiminterface)；再调用usb.bulkTransfer接口。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [bulkTransfer](arkts-basicservices-usbmanager-bulktransfer-f.md#bulktransfer)

<!--Device-usb-function bulkTransfer(    pipe: USBDevicePipe,    endpoint: USBEndpoint,    buffer: Uint8Array,    timeout?: number  ): Promise<number>--><!--Device-usb-function bulkTransfer(    pipe: USBDevicePipe,    endpoint: USBEndpoint,    buffer: Uint8Array,    timeout?: number  ): Promise<number>-End-->

**系统能力：** SystemCapability.USB.USBManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pipe | [USBDevicePipe](arkts-basicservices-usbmanager-usbdevicepipe-i.md) | 是 | 用于确定设备。 |
| endpoint | [USBEndpoint](arkts-basicservices-usbmanager-usbendpoint-i.md) | 是 | 用于确定传输的端口。 |
| buffer | Uint8Array | 是 | 用于写入或读取的缓冲区。 |
| timeout | number | 否 | 超时时间（单位：ms），可选参数，默认为0不超时。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，获取传输或接收到的数据块大小。失败返回-1。 |

**示例：**

```TypeScript
//usb.getDevices 接口返回数据集合，取其中一个设备对象，并获取权限 。
//把获取到的设备对象作为参数传入usb.connectDevice;当usb.connectDevice接口成功返回之后；
//才可以调用第三个接口usb.claimInterface.当usb.claimInterface 调用成功以后,再调用该接口。
usb.bulkTransfer(devicepipe, endpoint, buffer).then((ret) => {
 console.info(`bulkTransfer = ${ret}`);
});

```

