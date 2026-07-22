# getDevices

## 导入模块

```TypeScript
import { usb } from '@kit.BasicServicesKit';
```

## getDevices

```TypeScript
function getDevices(): Array<Readonly<USBDevice>>
```

获取USB设备列表。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getDevices](arkts-basicservices-usbmanager-getdevices-f.md#getdevices)

<!--Device-usb-function getDevices(): Array<Readonly<USBDevice>>--><!--Device-usb-function getDevices(): Array<Readonly<USBDevice>>-End-->

**系统能力：** SystemCapability.USB.USBManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;Readonly&lt;USBDevice&gt;&gt; | 设备信息列表。 |

**示例：**

```TypeScript
let devicesList = usb.getDevices();
console.info(`devicesList = ${devicesList}`);
// devicesList  返回的数据结构
// 此处提供一个简单的示例，如下
/*
  [
    {
      name: "1-1",
      serial: "",
      manufacturerName: "",
      productName: "",
      version: "",
      vendorId: 7531,
      productId: 2,
      clazz: 9,
      subClass: 0,
      protocol: 1,
      devAddress: 1,
      busNum: 1,
      configs: [
        {
          id: 1,
          attributes: 224,
          isRemoteWakeup: true,
          isSelfPowered: true,
          maxPower: 0,
          name: "1-1",
          interfaces: [
            {
              id: 0,
              protocol: 0,
              clazz: 9,
              subClass: 0,
              alternateSetting: 0,
              name: "1-1",
              endpoints: [
                {
                  address: 129,
                  attributes: 3,
                  interval: 12,
                  maxPacketSize: 4,
                  direction: 128,
                  number: 1,
                  type: 3,
                  interfaceId: 0,
                },
              ],
            },
          ],
        },
      ],
    },
  ]
 */

```

