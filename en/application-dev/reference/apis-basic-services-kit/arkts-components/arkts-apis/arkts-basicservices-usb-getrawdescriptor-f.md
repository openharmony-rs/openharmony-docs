# getRawDescriptor

## Modules to Import

```TypeScript
import { usb } from '@kit.BasicServicesKit';
```

## getRawDescriptor

```TypeScript
function getRawDescriptor(pipe: USBDevicePipe): Uint8Array
```

Obtains the raw USB descriptor.

Before you do this, call [usb.getDevices](arkts-basicservices-usb-getdevices-f.md) to obtain the USB device list, call [usb.requestRight](arkts-basicservices-usb-requestright-f.md) to request the device access permission, and call [usb.connectDevice](arkts-basicservices-usb-connectdevice-f.md) to obtain **devicepipe** as an input parameter.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getRawDescriptor](arkts-basicservices-usbmanager-getrawdescriptor-f.md)

**System capability:** SystemCapability.USB.USBManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pipe | [USBDevicePipe](arkts-basicservices-usb-usbdevicepipe-i.md) | Yes | Device pipe, which is used to determine the bus number and device address. |

**Return value:**

| Type | Description |
| --- | --- |
| Uint8Array | Returns the raw USB descriptor if the operation is successful; returns **undefined** otherwise. |

**Examples**

```TypeScript
let ret = usb.getRawDescriptor(devicepipe);
```
