# getPorts (System API)

## Modules to Import

```TypeScript
import { usb } from '@kit.BasicServicesKit';
```

## getPorts

```TypeScript
function getPorts(): Array<USBPort>
```

Obtains the list of all physical USB ports.

**Since:** 9

**Deprecated since:** 9

**Substitutes:** [getPorts](arkts-basicservices-usbmanager-getports-f-sys.md)

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[USBPort](arkts-basicservices-usb-usbport-i-sys.md)&gt; | List of physical USB ports. |

**Examples**

```TypeScript
let ret = usb.getPorts();
```
