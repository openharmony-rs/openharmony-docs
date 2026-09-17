# getCurrentFunctions (System API)

## Modules to Import

```TypeScript
import { usb } from '@kit.BasicServicesKit';
```

## getCurrentFunctions

```TypeScript
function getCurrentFunctions(): FunctionType
```

Obtains the numeric mask combination for the USB function list in Device mode.

**Since:** 9

**Deprecated since:** 9

**Substitutes:** [getCurrentFunctions](arkts-basicservices-usbmanager-getcurrentfunctions-f-sys.md)

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [FunctionType](arkts-basicservices-usb-functiontype-e-sys.md) | Numeric mask combination for the USB function list. |

**Examples**

```TypeScript
let ret = usb.getCurrentFunctions();
```
