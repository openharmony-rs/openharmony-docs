# removeRight

## Modules to Import

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## removeRight

```TypeScript
function removeRight(deviceName: string): boolean
```

Removes the permission for an app to access the device. System apps are granted the device access permission by default, and calling this API will not revoke the permission.

**Since:** 9

**System capability:** SystemCapability.USB.USBManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceName | string | Yes | Device name, which is the name of the USBDevice in the device list obtained by [getDevices](arkts-basicservices-usbmanager-getdevices-f.md). |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns the result of permission removal. The value **true** indicates that the permission is removed successfully; the value **false** indicates that the permission removal fails. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified.  <br>2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |

**Examples**

```TypeScript
function removeRight(): boolean {
  let devicesList: Array<usbManager.USBDevice> = usbManager.getDevices();
  if (!devicesList || devicesList.length == 0) {
    console.info(`device list is empty`);
    return false;
  }

  let device: usbManager.USBDevice = devicesList?.[0];
  if (usbManager.removeRight(device.name)) {
    console.info(`Succeed in removing right`);
    return true;
  }
  return false;
}
```
