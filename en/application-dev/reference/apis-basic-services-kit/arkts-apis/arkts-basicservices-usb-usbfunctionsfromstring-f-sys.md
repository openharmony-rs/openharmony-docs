# usbFunctionsFromString (System API)

## Modules to Import

```TypeScript
import { usb } from '@kit.BasicServicesKit';
```

## usbFunctionsFromString

```TypeScript
function usbFunctionsFromString(funcs: string): number
```

Converts the USB function list in the string format to a numeric mask in Device mode.

**Since:** 9

**Deprecated since:** 9

**Substitutes:** [usbFunctionsFromString](arkts-basicservices-usbmanager-usbfunctionsfromstring-f-sys.md)

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| funcs | string | Yes | Function list in string format. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Function list in numeric mask format after conversion. |

**Examples**

```TypeScript
let funcs = "acm";
let ret = usb.usbFunctionsFromString(funcs);
```
