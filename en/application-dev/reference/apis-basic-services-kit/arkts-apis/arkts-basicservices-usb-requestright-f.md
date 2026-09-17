# requestRight

## Modules to Import

```TypeScript
import { usb } from '@kit.BasicServicesKit';
```

## requestRight

```TypeScript
function requestRight(deviceName: string): Promise<boolean>
```

Requests the temporary permission for the application to access a USB device. This API uses a promise to return the result. System applications are granted the device access permission by default, and you do not need to apply for the permission separately.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [requestRight](arkts-basicservices-usbmanager-requestright-f.md)

**System capability:** SystemCapability.USB.USBManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceName | string | Yes | Device name. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the temporary device access permissions are granted; and the value **false** indicates the opposite. |

**Examples**

```TypeScript
let devicesName= "1-1";
usb.requestRight(devicesName).then((ret) => {
  console.info(`requestRight = ${ret}`);
});
```
