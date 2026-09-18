# bulkTransfer

## Modules to Import

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

Performs bulk transfer.

Before you do this, call [usb.getDevices](arkts-basicservices-usb-getdevices-f.md) to obtain the USB device list and endpoints, call [usb.requestRight](arkts-basicservices-usb-requestright-f.md) to request the device access permission, call [usb.connectDevice](arkts-basicservices-usb-connectdevice-f.md) to obtain **devicepipe** as an input parameter, and call [usb.claimInterface](arkts-basicservices-usb-claiminterface-f.md) to claim the USB interface.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [bulkTransfer](arkts-basicservices-usbmanager-bulktransfer-f.md)

**System capability:** SystemCapability.USB.USBManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pipe | [USBDevicePipe](arkts-basicservices-usb-usbdevicepipe-i.md) | Yes | USB device pipe, which is used to determine the USB device. |
| endpoint | [USBEndpoint](arkts-basicservices-usb-usbendpoint-i.md) | Yes | USB endpoint, which is used to determine the USB port for data transfer. |
| buffer | Uint8Array | Yes | Buffer for writing or reading data. |
| timeout | number | No | Timeout duration in ms. This parameter is optional. The default value is **0**, indicating no timeout. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the result, which is the size of the transmitted or received data block if the transfer is successful, or **-1** if an exception has occurred. |

**Examples**

```TypeScript
// Call usb.getDevices to obtain a data set. Then, obtain a USB device and its access permission.
// Pass the obtained USB device as a parameter to usb.connectDevice. Then, call usb.connectDevice to connect the USB device.
// Call usb.claimInterface to claim the USB interface. After that, call usb.bulkTransfer to start bulk transfer.
usb.bulkTransfer(devicepipe, endpoint, buffer).then((ret) => {
 console.info(`bulkTransfer = ${ret}`);
});
```
