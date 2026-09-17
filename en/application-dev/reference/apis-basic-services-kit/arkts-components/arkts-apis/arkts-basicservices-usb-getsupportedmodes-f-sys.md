# getSupportedModes (System API)

## Modules to Import

```TypeScript
import { usb } from '@kit.BasicServicesKit';
```

## getSupportedModes

```TypeScript
function getSupportedModes(portId: number): PortModeType
```

Obtains the mask combination for the supported mode list of a given USB port.

**Since:** 9

**Deprecated since:** 9

**Substitutes:** [getSupportedModes](arkts-basicservices-usbmanager-getsupportedmodes-f-sys.md)

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| portId | number | Yes | Port number. |

**Return value:**

| Type | Description |
| --- | --- |
| [PortModeType](arkts-basicservices-usb-portmodetype-e-sys.md) | Mask combination for the supported mode list. |

**Examples**

```TypeScript
let ret = usb.getSupportedModes(0);
```
