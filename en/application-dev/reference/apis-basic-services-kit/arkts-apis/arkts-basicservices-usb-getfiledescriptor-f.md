# getFileDescriptor

## Modules to Import

```TypeScript
import { usb } from '@kit.BasicServicesKit';
```

## getFileDescriptor

```TypeScript
function getFileDescriptor(pipe: USBDevicePipe): number
```

Obtains the file descriptor.

Before you do this, call [usb.getDevices](arkts-basicservices-usb-getdevices-f.md) to obtain the USB device list, call [usb.requestRight](arkts-basicservices-usb-requestright-f.md) to request the device access permission, and call [usb.connectDevice](arkts-basicservices-usb-connectdevice-f.md) to obtain **devicepipe** as an input parameter.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getFileDescriptor](arkts-basicservices-usbmanager-getfiledescriptor-f.md)

**System capability:** SystemCapability.USB.USBManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pipe | [USBDevicePipe](arkts-basicservices-usb-usbdevicepipe-i.md) | Yes | Device pipe, which is used to determine the bus number and device address. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the file descriptor of the USB device if the operation is successful; returns **-1** otherwise. |

**Examples**

```TypeScript
let ret = usb.getFileDescriptor(devicepipe);
```
