# getDevices

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';
```

## getDevices

```TypeScript
function getDevices(): Array<Readonly<USBDevice>>
```

获取接入主设备的USB设备列表。调用成功后返回已连接设备的详细信息列表包括设备名称、厂商产品信息等。 > **说明：** > > 三方应用无法通过getDevices()接口直接获取serial字段的设备序列号信息（该字段对三方应用不可用）。如需获取序列号，需要在申请设备访问权限后，自行发起控制传输获取。

**起始版本：** 23

<!--Device-usbManager-function getDevices(): Array<Readonly<USBDevice>>--><!--Device-usbManager-function getDevices(): Array<Readonly<USBDevice>>-End-->

**系统能力：** SystemCapability.USB.USBManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;Readonly&lt;USBDevice&gt;&gt; | 设备信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

**示例**

```TypeScript
let devicesList: Array<usbManager.USBDevice> = usbManager.getDevices();
if (devicesList) {
  console.info(`devicesList = ${JSON.stringify(devicesList)}`);
}
/*
  devicesList 返回的数据结构，此处提供一个简单的示例，如下
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

