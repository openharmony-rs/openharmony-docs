# getDevices

## getDevices

```TypeScript
function getDevices(): Array<Readonly<USBDevice>>
```

��ȡ�������豸��USB�豸�б���

> **˵����**
>
> ����Ӧ��û��Ȩ�޻�ȡserial�ֶζ�ȡ�豸���кţ���Ҫͨ��
> [usbManager.requestRight](arkts-basicservices-usbmanager-requestright-f.md#requestRight-1)����Ȩ�޺����з�����ƴ����ȡ��

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;Readonly&lt;USBDevice&gt;&gt; | �豸��Ϣ�б��� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.&lt;br&gt;**适用版本：** 18+ |

**示例：**

```TypeScript
let devicesList: Array<usbManager.USBDevice> = usbManager.getDevices();
console.info(`devicesList = ${devicesList}`);
/*
  devicesList 返回的数据结构,此处提供一个简单的示例，如下
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

