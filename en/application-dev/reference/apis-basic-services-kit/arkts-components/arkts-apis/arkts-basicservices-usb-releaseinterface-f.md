# releaseInterface

## Modules to Import

```TypeScript
import { usb } from '@kit.BasicServicesKit';
```

## releaseInterface

```TypeScript
function releaseInterface(pipe: USBDevicePipe, iface: USBInterface): number
```

Releases a USB interface.

Before you do this, ensure that you have claimed the interface by calling [usb.claimInterface](arkts-basicservices-usb-claiminterface-f.md).

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [releaseInterface](arkts-basicservices-usbmanager-releaseinterface-f.md)

**System capability:** SystemCapability.USB.USBManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pipe | [USBDevicePipe](arkts-basicservices-usb-usbdevicepipe-i.md) | Yes | Device pipe, which is used to determine the bus number and device address. |
| iface | [USBInterface](arkts-basicservices-usb-usbinterface-i.md) | Yes | USB interface, which is used to determine the index of the interface to release. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns **0** if the USB interface is successfully released; returns an error code otherwise. |

**Examples**

```TypeScript
let ret = usb.releaseInterface(devicepipe, interfaces);
console.info(`releaseInterface = ${ret}`);
```
