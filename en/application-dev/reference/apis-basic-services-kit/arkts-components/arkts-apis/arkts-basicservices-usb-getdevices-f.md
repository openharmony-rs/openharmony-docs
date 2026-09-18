# getDevices

## Modules to Import

```TypeScript
import { usb } from '@kit.BasicServicesKit';
```

## getDevices

```TypeScript
function getDevices(): Array<Readonly<USBDevice>>
```

Obtains the USB device list.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getDevices](arkts-basicservices-usbmanager-getdevices-f.md)

**System capability:** SystemCapability.USB.USBManager

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;Readonly&lt;[USBDevice](arkts-basicservices-usb-usbdevice-i.md)&gt;&gt; | USB device list. |

**Examples**

```TypeScript
let devicesList = usb.getDevices();
console.info(`devicesList = ${devicesList}`);
// devicesList is a list of USB devices.
// A simple example of devicesList is provided as follows:
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
