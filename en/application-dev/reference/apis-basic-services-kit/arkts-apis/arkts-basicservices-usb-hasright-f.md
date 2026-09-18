# hasRight

## Modules to Import

```TypeScript
import { usb } from '@kit.BasicServicesKit';
```

## hasRight

```TypeScript
function hasRight(deviceName: string): boolean
```

Checks whether the application has the permission to access the device.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [hasRight](arkts-basicservices-usbmanager-hasright-f.md)

**System capability:** SystemCapability.USB.USBManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceName | string | Yes | Device name. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the application has the permission to access the device; returns **false** otherwise. |

**Examples**

```TypeScript
let devicesName= "1-1";
let bool = usb.hasRight(devicesName);
console.info(`hasRight = ${bool}`);
```
