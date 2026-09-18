# setPortRoles (System API)

## Modules to Import

```TypeScript
import { usb } from '@kit.BasicServicesKit';
```

## setPortRoles

```TypeScript
function setPortRoles(portId: number, powerRole: PowerRoleType, dataRole: DataRoleType): Promise<boolean>
```

Sets the role types supported by a specified port, which can be **powerRole** (for charging) and **dataRole** (for data transfer).

**Since:** 9

**Deprecated since:** 9

**Substitutes:** [setPortRoles](arkts-basicservices-usbmanager-setportroles-f-sys.md)

**System capability:** SystemCapability.USB.USBManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| portId | number | Yes | Port number. |
| powerRole | [PowerRoleType](arkts-basicservices-usb-powerroletype-e-sys.md) | Yes | Role for charging. |
| dataRole | [DataRoleType](arkts-basicservices-usb-dataroletype-e-sys.md) | Yes | Role for data transfer. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the operation is successful, and **false** indicates the opposite. |

**Examples**

```TypeScript
let portId = 1;
usb.setPortRoles(portId, usb.PowerRoleType.SOURCE, usb.DataRoleType.HOST).then(() => {
    console.info('usb setPortRoles successfully.');
}).catch((err : BusinessError) => {
    console.error('usb setPortRoles failed: ' + err.code + ' message: ' + err.message);
});
```
