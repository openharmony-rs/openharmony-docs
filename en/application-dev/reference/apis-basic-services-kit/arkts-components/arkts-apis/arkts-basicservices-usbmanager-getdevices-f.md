# getDevices

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## getDevices

```TypeScript
function getDevices(): Array<Readonly<USBDevice>>
```

Obtains the list of USB devices connected to the host. After the API is called successfully, a list of connected devices is returned, including the device name, manufacturer, and product information.

> **NOTE:** 
> 
> Third-party apps cannot directly obtain the device serial number from the **serial** field
> through the **getDevices()** API. This field is unavailable to third-party apps. To obtain
> the serial number, third-party apps need to request permissions to access the device and
> then initiate a control transfer.

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;Readonly&lt;[USBDevice](arkts-basicservices-usbmanager-usbdevice-i.md)&gt;&gt; | Device information list. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |

**Examples**

```TypeScript
let devicesList: Array<usbManager.USBDevice> = usbManager.getDevices();
console.info(`devicesList = ${devicesList}`);
/*
  The following is a simple example of the data structure for devicesList:
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
